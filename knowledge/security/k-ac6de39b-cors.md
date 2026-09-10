---
id: "k-ac6de39b"
title: "同源策略与 CORS"
category: "security"
tags: ["浏览器","HTTP","安全"]
status: "ready"
created: "2026-09-10"
updated: "2026-09-10"
aliases: ["跨域资源共享","同源策略"]
---

# 同源策略与 CORS

## 核心概念

同源由协议、主机、端口共同确定。浏览器限制跨源读取；CORS 通过服务端响应头授予读取权限。

## 原理与机制

部分请求直接发送，部分先发 OPTIONS 预检，检查方法和请求头权限。携带凭证需客户端启用 credentials，服务端允许具体 Origin 并返回允许凭证的头；动态 Origin 响应还需正确处理缓存。

## 适用边界与易错点

同站不等于同源。CORS 不能替代鉴权或 CSRF 防护；部分被限制读取的请求已在服务端执行。no-cors 通常只得到不可读的 opaque 响应。

## 参考资料

- [MDN：CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/CORS)

## 关联题目

- [什么是跨域，常用解决方式有哪些？](../../questions/security/q-c0308061-cross-origin.md)
- [Web 登录安全应采取哪些措施？](../../questions/security/q-069ffd4d-login-security.md)
