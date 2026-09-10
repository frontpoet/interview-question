---
id: "k-b2585295"
title: "浏览器存储与凭证载体"
category: "security"
tags: ["浏览器","安全","IndexedDB"]
status: "ready"
created: "2026-09-10"
updated: "2026-09-10"
aliases: []
scope: ["浏览器同源存储与 HTTP Cookie"]
---

# 浏览器存储与凭证载体

## 核心概念

Cookie 是 HTTP 状态载体；localStorage/sessionStorage 是同步键值存储；IndexedDB 保存结构化数据。Token 是凭证内容，不是一种存储 API。

## 原理与机制

符合范围与策略的 Cookie 随请求发送，可设 HttpOnly、Secure、SameSite。Web Storage 不自动附加到请求；localStorage 持久到显式删除或清理，sessionStorage 按源和顶层浏览上下文隔离。IndexedDB 支持异步索引查询和事务。

## 适用边界与易错点

客户端持久化可能受配额、隐私模式和驱逐影响。JS 可访问存储中的凭证可能被 XSS 窃取；HttpOnly 防止 JS 读取 Cookie，但不防止 XSS 发起已认证操作。

## 参考资料

- [MDN：Cookie](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Cookies)
- [MDN：存储配额与清理](https://developer.mozilla.org/en-US/docs/Web/API/Storage_API/Storage_quotas_and_eviction_criteria)

## 关联题目

- [Cookie、Web Storage、IndexedDB 与 Token 有何区别？](../../questions/security/q-b7ad08d9-browser-storage.md)
- [Web 登录安全应采取哪些措施？](../../questions/security/q-069ffd4d-login-security.md)
