---
id: "q-88b02c0b"
title: "Web Worker 最多能创建几个，线程间如何通信？"
category: "frameworks-tools"
tags: ["JavaScript","前端","并发"]
status: "ready"
type: "concept"
created: "2026-09-22"
updated: "2026-09-22"
scope: ["浏览器 Web Worker，不讨论 Node worker_threads 的资源选项"]
relations:
  examines: ["k-8849404b"]
---

# Web Worker 最多能创建几个，线程间如何通信？

## 题目

浏览器最多能有几个 Worker？主线程和 Worker、两个 Worker 之间如何通信？

## 简要回答

没有跨浏览器统一的固定最大值，实际受实现、内存、CPU 和资源策略约束。hardwareConcurrency 只能用于池大小的初始估计，不能据此断言最多只能创建同样数量的 Worker。

通信首选 postMessage，默认结构化克隆；大量二进制数据可转移 ArrayBuffer 所有权；需共享状态时在满足隔离条件后使用 SharedArrayBuffer + Atomics。两个 Worker 可通过主线程转发或 MessageChannel 通信。

## 分析与边界

函数、DOM 节点不能像普通 JSON 数据一样传递。transfer 后发送方不能继续使用已分离的缓冲区。Worker 能缓解计算阻塞，不能直接改变 DOM；应维护任务队列、错误与取消处理，避免每个小任务都创建一个实例。

## 相关知识点

- [Web Worker 并行计算与消息通信](../../knowledge/frameworks-tools/k-8849404b-web-workers.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-22-frontend-network-engineering.md)

