# JWT 认证方案决策

> 日期：2026-06-20
> 决策人：开发者
> 状态：已实施

## 背景

task-tracker 需要用户认证系统。需要在 JWT 和 Session 两种方案中选择。

## 方案对比

| 维度 | JWT | Session |
|------|-----|---------|
| 服务端状态 | 无状态，易于横向扩展 | 需要存储 session，扩展需共享存储 |
| 前端集成 | token 存 localStorage，简单 | cookie 自动携带，需处理 CSRF |
| 过期控制 | 通过 exp 声明控制，无法强制失效 | 服务端可随时销毁 |
| 当前需求匹配 | 单服务，无扩展需求但保持可选 | 需要额外引入 session 中间件 |

## 决策

选择 JWT 认证方案，理由：

1. 项目当前是单服务，但保留未来拆分前后端部署的灵活性。
2. 前端已是 React SPA，JWT + localStorage 集成简单。
3. 使用 `jsonwebtoken` + `bcrypt` 是 Node.js 生态成熟方案。

## 实施细则

- Token 有效期：24 小时
- 刷新策略：暂不实现 refresh token，过期后重新登录（未来按需添加）
- 中间件：全局鉴权中间件，排除 `/api/auth/*` 路由
- 密码存储：bcrypt hash，salt rounds = 10

## 影响范围

- 后端：auth 路由、JWT 中间件、用户模型
- 前端：登录/注册页面、API 请求拦截器（添加 Authorization header）
- 测试：所有需要认证的接口测试需携带有效 token
