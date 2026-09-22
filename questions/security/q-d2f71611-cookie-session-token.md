---
id: "q-d2f71611"
title: "Cookie、Session、Token 如何配合实现登录？"
category: "security"
tags: ["安全","HTTP"]
status: "ready"
type: "comparison"
created: "2026-09-22"
updated: "2026-09-22"
scope: ["Cookie 会话与 Bearer 凭证只是常见组合"]
relations:
  examines: ["k-648ba851"]
---

# Cookie、Session、Token 如何配合实现登录？

## 题目

用户登录有哪些常见实现？比较 Cookie、Session 和 Token。

## 简要回答

三者不是同一维度：Cookie 是浏览器存储和自动发送状态的机制；Session 是服务端关联用户状态的会话方案；Token 是访问凭证，可为不透明字符串或 JWT。

| 维度 | Cookie 携带会话 ID | Bearer Token（以 JWT 为例） |
| --- | --- | --- |
| 登录后 | 服务端建会话，Set-Cookie 写入随机 ID | 签发访问令牌，客户端按约定保存 |
| 请求校验 | 读 ID、查询会话并检查权限 | 校验签名、期限、签发者和受众，再检查权限 |
| 注销撤销 | 删除或失效会话 | 短有效期配合刷新令牌撤销，必要时撤销列表 |
| 扩展 | 多实例共享会话或路由策略 | 可本地校验，但刷新、撤销等仍可能依赖状态 |

## 分析与边界

Token 也能放进 HttpOnly Cookie，Session ID 本身也可视作令牌，JWT 并非所有 Token 的必选格式。Cookie 凭证常自动随请求携带，需处理 CSRF；JS 可读令牌易受 XSS 窃取。HttpOnly 限制读取但不阻止 XSS 发起已认证请求。全链路 HTTPS，并在服务端执行授权。

## 相关知识点

- [登录认证与会话安全](../../knowledge/security/k-648ba851-auth.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-22-frontend-network-engineering.md)

