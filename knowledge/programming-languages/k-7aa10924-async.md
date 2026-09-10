---
id: "k-7aa10924"
title: "Promise 聚合与异步任务调度"
category: "programming-languages"
tags: ["JavaScript","Promise"]
status: "ready"
created: "2026-09-10"
updated: "2026-09-10"
aliases: []
scope: ["JavaScript；串行启动要求输入任务函数"]
---

# Promise 聚合与异步任务调度

## 核心概念

Promise 表示异步结果，不是可延迟启动的任务。任务函数 `() => Promise` 才能把启动时机交给调度器。

## 原理与机制

`Promise.all` 聚合可迭代对象中的结果，结果按输入顺序排列；任一项拒绝则聚合结果拒绝，但不会取消其他工作。并发常来自调用请求函数时就已启动工作。

串行调度每次调用一个任务函数，等待成功后再调用下一个。它适用于有顺序约束或需要限制并发的操作，总代价接近各任务耗时之和。

## 适用边界与易错点

依次 `await` 已创建的 Promise 只能控制等待顺序。失败后不启动剩余任务与 `Promise.all` 中其他任务继续运行，是额外的行为差异。取消需另行传递 AbortSignal。

## 参考资料

- [MDN：Promise.all](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/all)

## 关联题目

- [如何串行执行异步任务并按顺序返回结果？](../../questions/programming-languages/q-06ed975d-serial-promises.md)
