---
id: "k-8849404b"
title: "Web Worker 并行计算与消息通信"
category: "frameworks-tools"
tags: ["JavaScript","前端","并发"]
status: "ready"
created: "2026-09-22"
updated: "2026-09-22"
---

# Web Worker 并行计算与消息通信

## 核心概念

Worker 在独立执行环境运行脚本，使主线程能继续处理界面；它不能直接操作 DOM，也不等于一个固定可见的物理 CPU 核心。

## 原理与机制

主线程与 Worker 用 postMessage/onmessage 通信，默认按结构化克隆传值。传输 ArrayBuffer 的所有权可避免复制，发送端缓冲区会被分离；SharedArrayBuffer 共享内存通常要求安全上下文与跨源隔离，用 Atomics 协调并发访问。两个 Worker 可经主线程中转，也可传递 MessageChannel 的端口直接通信。

## 适用边界与易错点

标准没有给出所有浏览器通用的最大创建数量。navigator.hardwareConcurrency 是浏览器报告的可用逻辑处理器数，可能被降低，不是 Worker 配额。Worker 的启动与内存成本不低，应复用有界池，以吞吐、响应性和内存实测调节；I/O 等待通常不必专门建 Worker。任务协议需 ID、结果/错误和取消语义，完成后及时 terminate 或复用。

## 参考资料

- [WHATWG：Web workers，含并发硬件提示](https://html.spec.whatwg.org/multipage/workers.html)
- [MDN：SharedArrayBuffer 安全要求](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/SharedArrayBuffer)

## 关联题目

- [Web Worker 最多能创建几个，线程间如何通信？](../../questions/frameworks-tools/q-88b02c0b-worker-limits-messaging.md)

