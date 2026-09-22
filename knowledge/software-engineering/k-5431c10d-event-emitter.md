---
id: "k-5431c10d"
title: "发布订阅与事件监听生命周期"
category: "software-engineering"
tags: ["JavaScript","设计模式"]
status: "ready"
created: "2026-09-22"
updated: "2026-09-22"
---

# 发布订阅与事件监听生命周期

## 核心概念

事件发射器维护“事件名 → 回调集合”，使订阅方与触发方通过事件解耦。它是进程内同步分发的一种模式，不自带跨网络可靠交付能力。

## 原理与机制

on 注册，emit 触发，off 取消。触发时对回调集合取快照，可固定本轮执行顺序，避免回调内增删导致遍历行为不清晰。订阅需要成对清理，或返回只取消自身注册的函数。重复注册、once、错误传播、this 和异步监听器返回值都应写入契约。

## 适用边界与易错点

不同库的语义不相同：Node EventEmitter 的重复注册、error 事件等有特殊行为，简化实现不能冒称兼容。同步抛错可选择立即传播或隔离汇总；若采用传播策略，本轮后续监听器不会执行。快照策略下，在本轮取消的监听器仍可能已排入本轮执行。

## 参考资料

- [Node.js：EventEmitter](https://nodejs.org/api/events.html#class-eventemitter)

## 关联题目

- [如何实现 EventEmitter 的 on、call 和 off？](../../questions/programming-languages/q-836204b0-event-emitter.md)

