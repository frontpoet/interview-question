---
id: "q-4dc59b7e"
title: "本地存储为什么选择 SQLite，而不是 IndexedDB？"
category: "databases"
tags: ["SQLite","IndexedDB"]
status: "draft"
type: "scenario"
created: "2026-09-10"
updated: "2026-09-10"
scope: ["按复杂关系查询和跨浏览器/Node/客户端需求分析；实际项目环境待确认"]
relations:
  examines: ["k-4834a977"]
---

# 本地存储为什么选择 SQLite，而不是 IndexedDB？

## 题目

结合查询模型、事务、运行环境和维护成本说明选型。

## 简要回答

| 维度 | SQLite | IndexedDB |
| --- | --- | --- |
| 数据与查询 | 关系表、SQL、JOIN、约束 | 对象存储、键、索引、游标 |
| 事务和索引 | 支持 | 同样支持，API 和事务生命周期不同 |
| 运行环境 | 可嵌入客户端、Node 等；浏览器需适配 | 浏览器原生，绑定 Web 存储环境 |
| 集成成本 | 驱动或 WASM、迁移和持久化适配 | 原生 API 或封装库、schema 升级 |

若复杂表关联、多条件查询和 SQL 复用是主要需求，可选 SQLite。纯浏览器的缓存、离线数据、草稿或文件管理，且关联查询简单时，可优先评估 IndexedDB。

## 分析与边界

“SQLite 索引成熟、事务强”不能推导“IndexedDB 不支持这些能力”。跨平台复用还需封装存储接口；浏览器 SQLite 仍受持久化支持和配额约束。并发写、数据量、迁移和部署成本均须评估。

## 待确认

实际运行在纯浏览器、Electron、Node 还是移动客户端？是否已有复杂关联查询与跨端复用需求？当前保留为选型框架，不认定为用户项目事实。

## 相关知识点

- [SQLite 与 IndexedDB 的本地存储模型](../../knowledge/databases/k-4834a977-local-db.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-10-frontend-and-os.md)
