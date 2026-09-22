---
id: "k-648ba851"
title: "登录认证与会话安全"
category: "security"
tags: ["安全","HTTP"]
status: "ready"
created: "2026-09-10"
updated: "2026-09-22"
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

### Cookie、Session 与 Token 的组合

Cookie 是状态载体，Session 是维护会话状态的机制，Token 是凭证。常见会话流程为：验证登录 → 生成高熵随机会话 ID → 服务端保存关联用户、期限和权限状态 → Set-Cookie → 后续请求查会话 → 退出时失效会话并清除 Cookie。会话 ID 应轮换，不能把用户 ID 当作不可猜测的凭证。

另一方案使用不透明访问令牌或签名 JWT。JWT 需验证签名、允许的算法、期限、签发者和受众；它通常是签名而非加密，载荷不能随意放秘密。令牌可放 HttpOnly Cookie 或按约定由客户端通过 Authorization 发送，载体决定相关威胁边界，不能说“Token 天然不会 CSRF”。

自包含令牌不自动提供即时撤销，可通过短有效期、刷新令牌轮换和服务端撤销状态控制。多实例 Session 通常需要共享会话存储；JWT 方案也可能需要刷新、权限变更和撤销状态。

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
- [Cookie、Session、Token 如何配合实现登录？](../../questions/security/q-d2f71611-cookie-session-token.md)
