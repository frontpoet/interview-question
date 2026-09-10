---
id: "k-4834a977"
title: "SQLite 与 IndexedDB 的本地存储模型"
category: "databases"
tags: ["SQLite","IndexedDB"]
status: "ready"
created: "2026-09-10"
updated: "2026-09-10"
aliases: []
scope: ["SQLite 嵌入式数据库；浏览器 IndexedDB"]
---

# SQLite 与 IndexedDB 的本地存储模型

## 核心概念

SQLite 是支持 SQL 的嵌入式关系数据库；IndexedDB 是浏览器提供的异步对象存储数据库，支持索引和事务。

## 原理与机制

SQLite 使用表、约束、连接查询和事务表达关系数据，适合本地应用和跨运行时复用 SQL。IndexedDB 使用 object store、键、索引和游标，事务有指定作用域和生命周期，复杂关联通常由应用组合查询。

## 适用边界与易错点

IndexedDB 不是“无索引、无事务”。SQLite 通常同一数据库同时只有一个写事务，高并发写入要评估。浏览器运行 SQLite 需 WASM 和持久化适配，可能使用 OPFS；仍受浏览器能力、配额和清理策略约束。

## 参考资料

- [SQLite：适用场景](https://sqlite.org/whentouse.html)
- [MDN：IndexedDB](https://developer.mozilla.org/en-US/docs/Web/API/IndexedDB_API)
- [SQLite WASM：持久化](https://www.sqlite.org/wasm/doc/trunk/persistence.md)

## 关联题目

- [本地存储为什么选择 SQLite，而不是 IndexedDB？](../../questions/databases/q-4dc59b7e-sqlite-indexeddb.md)
- [Cookie、Web Storage、IndexedDB 与 Token 有何区别？](../../questions/security/q-b7ad08d9-browser-storage.md)
