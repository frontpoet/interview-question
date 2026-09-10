---
id: "k-8166fabc"
title: "灰度发布与功能开关"
category: "software-engineering"
tags: ["发布","前端"]
status: "ready"
created: "2026-09-10"
updated: "2026-09-10"
aliases: ["渐进发布","Feature Flag"]
---

# 灰度发布与功能开关

## 核心概念

灰度发布按稳定规则向部分用户提供新版本。功能开关控制行为，资源版本控制代码分发，两者可配合使用。

## 原理与机制

以用户或租户标识加开关盐做稳定分桶；分阶段增加比例，按版本和分组比较错误率、关键业务指标和性能。配置异常使用约定默认值，保留快速关闭开关与回滚入口。

## 适用边界与易错点

前端开关不能替代服务端授权。缓存键、HTML、资源清单和 Service Worker 需保持版本一致；接口与数据迁移需允许新旧客户端共存。

## 参考资料

- [OpenFeature：功能开关接口与上下文](https://openfeature.dev/docs/reference/intro/)

## 关联题目

- [如何实施前端灰度发布？](../../questions/system-design/q-5237f1de-frontend-canary.md)
