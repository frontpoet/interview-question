---
id: "q-fdff17bf"
title: "如何设计前端异常监控系统？"
category: "system-design"
tags: ["前端","监控"]
status: "ready"
type: "scenario"
created: "2026-09-10"
updated: "2026-09-10"
scope: ["浏览器 SDK、接收服务、聚合存储与告警组成的方案"]
relations:
  examines: ["k-f98cfc36"]
---

# 如何设计前端异常监控系统？

## 题目

覆盖采集、上报、定位、告警以及 SDK 的性能和隐私约束。

## 简要回答

- 采集脚本 error、资源失败、unhandledrejection；结合框架错误边界与请求封装记录接口问题。
- 附时间、路由、release、浏览器环境、脱敏操作轨迹及 trace/request ID；不记录密码或完整令牌。
- 客户端去重、采样、限流、批量上报；离开页面时可用 sendBeacon 或受限的 keepalive 请求，不保证一定送达。
- 服务端校验大小和结构，按堆栈指纹聚合，用匹配 release 的私有 source map 还原位置。
- 告警同时看影响用户数、错误率和新版本回归，提供检索、趋势、分派和修复后验证。

## 分析与边界

SDK 需隔离自身异常，排除上报接口递归采集，限制缓存和重试。资源 error 需捕获阶段监听；跨域脚本可能仅有有限错误信息。Error Boundary 不能覆盖所有事件和异步错误，客户端上报内容也不能当可信输入。

## 相关知识点

- [前端异常采集与可观测性](../../knowledge/software-engineering/k-f98cfc36-observability.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-10-frontend-and-os.md)
