# CORS 配置遗漏复盘

> 日期：2026-06-15
> 发现人：开发者
> 影响范围：前端开发环境

## 现象

前端（localhost:3000）调用后端 API（localhost:8080）时浏览器报错：

```
Access to fetch at 'http://localhost:8080/api/auth/login' from origin
'http://localhost:3000' has been blocked by CORS policy
```

## 原因

后端 Express 应用初始化时只配置了路由和中间件，遗漏了 CORS 配置。前端开发服务器和后端 API 使用不同端口，浏览器阻止跨域请求。

## 修复

在后端 `server/src/index.ts` 中添加：

```typescript
import cors from 'cors';

app.use(cors({
  origin: ['http://localhost:3000'],
  credentials: true,
}));
```

同时在 `package.json` 中添加 `cors` 依赖。

## 避免方式

1. 新项目初始化检查清单中加入"CORS 配置确认"一项。
2. 前端和后端使用不同端口时，必须在后端明确配置 CORS 白名单。
3. 生产环境部署时确认 CORS origin 是否更新为实际域名。

## 相关经验

- 受保护文件：`package.json`（依赖变更需谨慎）
- 每次新增前后端分离项目时，第一步就确认 CORS 配置
