---
id: "q-b7ad08d9"
title: "Cookie、Web Storage、IndexedDB 与 Token 有何区别？"
category: "security"
tags: ["浏览器","安全","IndexedDB"]
status: "ready"
type: "comparison"
created: "2026-09-10"
updated: "2026-09-10"
scope: ["浏览器同源存储与 HTTP Cookie","SQLite 嵌入式数据库；浏览器 IndexedDB"]
relations:
  examines: ["k-b2585295","k-4834a977"]
---

# Cookie、Web Storage、IndexedDB 与 Token 有何区别？

## 题目

比较存储用途、生命周期和请求行为，解释 Cookie 与 Token 的关系。

## 简要回答

| 机制 | 用途和特点 |
| --- | --- |
| Cookie | 小规模 HTTP 状态，按范围与策略自动随请求发送 |
| localStorage | 同步字符串键值存储，跨页面会话保留至删除或清理 |
| sessionStorage | 同步字符串存储，按源和顶层浏览上下文隔离，刷新通常保留 |
| IndexedDB | 异步结构化存储，支持索引、事务及 Blob |
| Token | 凭证内容，可放 Cookie、内存或其他载体，本身不是存储机制 |

登录状态选型需结合 XSS、CSRF、过期和撤销。JWT 通常是签名数据，不能当加密容器；不要将敏感数据放进去后假定不可读取。大量业务数据不适合放 Cookie 随请求反复传输。

## 相关知识点

- [浏览器存储与凭证载体](../../knowledge/security/k-b2585295-storage.md)
- [SQLite 与 IndexedDB 的本地存储模型](../../knowledge/databases/k-4834a977-local-db.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-10-frontend-and-os.md)
