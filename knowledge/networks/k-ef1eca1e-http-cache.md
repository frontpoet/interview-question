---
id: "k-ef1eca1e"
title: "HTTP 缓存与静态资源版本"
category: "networks"
tags: ["HTTP","构建","性能"]
status: "ready"
created: "2026-09-10"
updated: "2026-09-10"
aliases: []
---

# HTTP 缓存与静态资源版本

## 核心概念

缓存按新鲜度复用响应，过期后可用验证器确认资源是否变化。内容哈希用于区分不可变资源版本。

## 原理与机制

Cache-Control 指定缓存策略，ETag/If-None-Match 等支持验证。带内容哈希的静态资源可长缓存，HTML 和版本清单需及时验证或短缓存，使入口能指向新版本。

## 适用边界与易错点

no-cache 允许存储但复用前需验证；no-store 禁止存储。个性化响应不可误放共享缓存。发布新版本时保留旧资源，防止已打开页面后续加载旧 chunk 失败。

## 参考资料

- [MDN：HTTP 缓存](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Caching)

## 关联题目

- [如何系统优化首屏、请求、渲染和打包性能？](../../questions/frameworks-tools/q-c374ef0f-frontend-optimization.md)
- [如何实施前端灰度发布？](../../questions/system-design/q-5237f1de-frontend-canary.md)
