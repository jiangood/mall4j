# Nginx 配置

Nginx 常用于两个场景：

- 托管管理后台静态文件。
- 反向代理后端接口。

## 管理后台

管理后台构建：

```powershell
cd front-end\mall4v
pnpm run build
```

将构建产物部署到 Nginx 静态目录，例如：

```text
/usr/share/nginx/admin
```

## 反向代理

管理后台接口代理到：

```text
yami-shop-admin:8085
```

用户端接口代理到：

```text
yami-shop-api:8086
```

示例结构：

```nginx
server {
    listen 80;
    server_name admin.example.com;

    root /usr/share/nginx/admin;
    index index.html;

    location / {
        try_files $uri $uri/ /index.html;
    }

    location /api/ {
        proxy_pass http://127.0.0.1:8085/;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }
}
```

如果前端 `VITE_APP_BASE_API` 直接写完整后端地址，则不一定需要 `/api/` 代理；如果写相对路径，则需要 Nginx 配合。

## `/apis` 转发方式

旧部署文档里使用过 `/apis` 前缀来减少后台接口域名数量。当前 `front-end/mall4v/.env.production` 默认仍是完整地址：

```text
VITE_APP_BASE_API = 'http://127.0.0.1:8085'
```

如果生产环境希望改成相对路径，例如：

```text
VITE_APP_BASE_API = '/apis'
```

则需要在 Nginx 增加对应转发：

```nginx
location /apis {
    rewrite ^/apis/(.*)$ /$1 break;
    proxy_pass http://127.0.0.1:8111;
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
}
```

其中 `8111` 来自当前 `yami-shop-admin` 的 `application-prod.yml`。如果生产端口改了，Nginx 也要同步改。

## 注意事项

- 管理后台只能连管理端接口 `8085`。
- 小程序、H5、uni-app 只能连用户端接口 `8086`。
- 微信小程序正式环境通常要求 HTTPS 域名。
- 接入支付回调时，回调域名必须能被第三方支付平台访问。
