---
id: "k-f98cfc36"
title: "前端异常采集与可观测性"
category: "software-engineering"
tags: ["监控","前端"]
status: "ready"
created: "2026-09-10"
updated: "2026-09-10"
aliases: ["前端监控","异常监控"]
---

# 前端异常采集与可观测性

## 核心概念

异常监控包括采集、上下文关联、上报、聚合和告警。错误日志与性能追踪相互补充。

## 原理与机制

error 采集脚本异常和捕获阶段的资源失败，unhandledrejection 采集未处理拒绝；请求封装记录 HTTP 状态、超时和业务错误。以 release、路由、堆栈、trace ID 关联问题，用匹配版本的 source map 还原位置。

## 适用边界与易错点

框架错误边界不能覆盖全部事件处理、异步和资源错误。采样、限流、脱敏及 SDK 自身异常隔离不可省略；跨域脚本可能缺少完整堆栈。上报失败应有有界重试，避免递归采集。

## 参考资料

- [MDN：error](https://developer.mozilla.org/en-US/docs/Web/API/Window/error_event)
- [MDN：unhandledrejection](https://developer.mozilla.org/en-US/docs/Web/API/Window/unhandledrejection_event)
- [OpenTelemetry：浏览器观测](https://opentelemetry.io/docs/languages/js/getting-started/browser/)

## 关联题目

- [如何实施前端灰度发布？](../../questions/system-design/q-5237f1de-frontend-canary.md)
- [如何设计前端异常监控系统？](../../questions/system-design/q-fdff17bf-frontend-errors.md)
