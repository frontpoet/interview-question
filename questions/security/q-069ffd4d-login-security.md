---
id: "q-069ffd4d"
title: "Web 登录安全应采取哪些措施？"
category: "security"
tags: ["安全","HTTP"]
status: "ready"
type: "scenario"
created: "2026-09-10"
updated: "2026-09-10"
scope: ["常规浏览器 Web 应用；Cookie 会话与 Token 架构分别评估"]
relations:
  examines: ["k-648ba851","k-b2585295","k-ac6de39b"]
---

# Web 登录安全应采取哪些措施？

## 题目

从登录入口、会话、前端和服务端说明安全措施。

## 简要回答

- 全程 HTTPS，登录限速和异常检测，避免通过不同错误文案泄露账号存在性；支持 MFA 或通行密钥。
- 密码在服务端用专用密码哈希方案保存，前端加密或哈希不能替代 HTTPS 和服务端密码保护。
- Cookie 会话设置 Secure、HttpOnly 和适合业务的 SameSite，限制 Domain/Path；根据请求场景提供 CSRF token 或来源校验。
- 登录、提权后轮换会话，设置过期、退出撤销和敏感操作再认证；Token 方案还需刷新、轮换和泄露处置。
- 防 XSS：按上下文转义、清理不可信 HTML、配合 CSP；每个敏感接口由服务端独立鉴权。

## 分析与边界

HttpOnly 不能阻止 XSS 借当前会话操作；SameSite 也不是所有场景下的完整 CSRF 防线。不要把令牌拼入 URL、日志或错误上报。会话存放位置应按认证架构决定，不把 localStorage 或 Cookie 宣称为绝对安全。

## 相关知识点

- [登录认证与会话安全](../../knowledge/security/k-648ba851-auth.md)
- [浏览器存储与凭证载体](../../knowledge/security/k-b2585295-storage.md)
- [同源策略与 CORS](../../knowledge/security/k-ac6de39b-cors.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-10-frontend-and-os.md)
