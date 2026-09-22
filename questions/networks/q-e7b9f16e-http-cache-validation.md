---
id: "q-e7b9f16e"
title: "HTTP 强缓存、协商缓存、no-cache 与 no-store 有何区别？"
category: "networks"
tags: ["HTTP","性能"]
status: "ready"
type: "comparison"
created: "2026-09-22"
updated: "2026-09-22"
scope: ["HTTP 缓存；以 GET 响应和无字段参数的 no-cache 为例"]
relations:
  examines: ["k-ef1eca1e"]
---

# HTTP 强缓存、协商缓存、no-cache 与 no-store 有何区别？

## 题目

解释 HTTP 缓存机制，以及 Cache-Control 中 no-cache、no-store 与协商缓存的关系。

## 简要回答

1. 可直接使用的新鲜缓存通常不发网络请求，常称“强缓存”；新鲜度主要由 max-age 或 Expires 决定。
2. 需要验证时，携带 ETag 对应的 If-None-Match，或 Last-Modified 对应的 If-Modified-Since 发起条件请求。
3. 未变化时服务端返回 304，客户端更新缓存元数据并复用原响应体；变化则通常返回 200 和新响应体。
4. no-cache 允许存储，但复用前必须成功验证；no-store 要求不要存储本次请求或响应的相关内容。
5. no-cache 不等于不缓存；no-store 不是清除历史缓存或阻止截图等存储行为的万能开关。

## 常见问法

原文的“nocatch、nostore”按 HTTP 指令规范为 `no-cache`、`no-store`。

## 分析与边界

协商缓存仍有网络往返；304 不包含本次资源正文。存在 If-None-Match 时优先按它处理验证。缓存键、Vary、private 与共享缓存的权限边界也影响能否复用。

## 相关知识点

- [HTTP 缓存与静态资源版本](../../knowledge/networks/k-ef1eca1e-http-cache.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-22-frontend-network-engineering.md)

