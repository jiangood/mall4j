# Mall4j Java 商城系统

Mall4j 是基于 Spring Boot 4 + Vue3 的 B2C 单商户商城系统，包含商品、订单、会员、规格/SKU、购物车、支付、权限、内容和统计等模块。

## 项目说明

- **技术栈**: Spring Boot 4, Sa-Token, MyBatis / MyBatis-Plus, Redis, Vue3
- **开源协议**: AGPLv3 — 适合学习、评估和符合协议要求的使用场景
- **商业版**: 覆盖 B2C、B2B2C、S2B2C、SaaS、多租户、跨境等场景，详见[官网](https://www.mall4j.com)

## 后端模块

| 模块 | 说明 |
| --- | --- |
| `yami-shop-admin` | 后台管理接口 |
| `yami-shop-api` | 前台 API 接口 |
| `yami-shop-bean` | 实体类 |
| `yami-shop-common` | 公共工具类 |
| `yami-shop-security` | 权限认证（admin/api/common） |
| `yami-shop-service` | 业务服务层 |
| `yami-shop-sys` | 系统管理 |

## 前端项目

| 项目 | 说明 |
| --- | --- |
| [mall4v](https://gitee.com/gz-yami/mall4v) | Vue3 管理后台 |
| [mall4m](https://gitee.com/gz-yami/mall4m) | 原生微信小程序 |
| [mall4uni](https://gitee.com/gz-yami/mall4uni) | uni-app 多端商城 |

## 技术选型

| 技术 | 说明 |
| --- | --- |
| Spring Boot 4.x | MVC 核心框架 |
| Sa-Token | 权限认证 |
| MyBatis / MyBatis-Plus | ORM 框架 |
| Redis / Redisson | 缓存与分布式锁 |
| spring-doc | 接口文档 |
| jakarta-validation | 参数校验 |
| HikariCP | 数据库连接池 |
| Logback | 日志 |
| Lombok | 简化代码 |
| Hutool | Java 工具集 |
| Knife4j | Swagger UI |

## 快速启动

数据库脚本：`db/yami_shop.sql`

开发环境搭建参考 [Gitee Wiki](https://gitee.com/gz-yami/mall4j/wikis) 或 [B站视频](https://www.bilibili.com/video/BV1eW4y1V7c1)。

## 授权说明

- **开源版**: B2C 单商户商城，遵循 AGPLv3 协议，可学习、研究、二次开发和自行部署
- **企业版**: 闭源商用、私有化部署、多商户/供应链/SaaS/跨境等场景，详见[官网](https://www.mall4j.com/price/)

## 相关仓库

| 仓库 | 说明 |
| --- | --- |
| [mall4j](https://gitee.com/gz-yami/mall4j) | 后端主仓库 |
| [mall4v](https://gitee.com/gz-yami/mall4v) | Vue3 管理后台 |
| [mall4m](https://gitee.com/gz-yami/mall4m) | 原生微信小程序 |
| [mall4uni](https://gitee.com/gz-yami/mall4uni) | uni-app 多端商城 |
| [mall4cloud](https://gitee.com/gz-yami/mall4cloud) | 微服务版 |

## 鸣谢

- [WxJava](https://github.com/Wechat-Group/WxJava)
- [Sa-Token](https://gitee.com/dromara/sa-token)
