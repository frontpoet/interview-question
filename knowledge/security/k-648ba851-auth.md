---
id: "k-648ba851"
title: "登录认证与会话安全"
category: "security"
tags: ["安全","HTTP"]
status: "ready"
created: "2026-09-10"
updated: "2026-09-10"
aliases: []
scope: ["浏览器 Web 应用；具体机制取决于认证架构"]
relations:
  prerequisite: ["k-b2585295","k-ac6de39b"]
---

# 登录认证与会话安全

## 核心概念

认证确认身份，授权判断权限，会话把后续请求关联到身份。安全措施需同时覆盖凭证、传输和服务端校验。

## 原理与机制

使用 HTTPS，限制登录尝试，提供 MFA 或通行密钥；服务端安全处理密码与恢复流程。登录或权限提升时轮换会话，设置空闲与绝对过期，支持撤销。敏感操作重新认证，Cookie 会话配合 CSRF 防护。

## 适用边界与易错点

前端隐藏按钮不等于授权，JWT 签名不等于加密。不要记录密码或完整令牌。Cookie 会话与 Bearer Token 的取舍依架构决定，不存在一种存放位置消除所有 XSS/CSRF 风险。

## 参考资料

- [OWASP：认证](https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html)
- [OWASP：会话管理](https://cheatsheetseries.owasp.org/cheatsheets/Session_Management_Cheat_Sheet.html)

## 前置知识

- [浏览器存储与凭证载体](k-b2585295-storage.md)
- [同源策略与 CORS](k-ac6de39b-cors.md)

## 关联题目

- [Web 登录安全应采取哪些措施？](../../questions/security/q-069ffd4d-login-security.md)
