---
id: "q-06ed975d"
title: "如何串行执行异步任务并按顺序返回结果？"
category: "programming-languages"
tags: ["JavaScript","Promise"]
status: "ready"
type: "coding"
created: "2026-09-10"
updated: "2026-09-10"
scope: ["采用任务函数数组，不接收已经启动的 Promise 数组；遇错停止"]
relations:
  examines: ["k-7aa10924"]
---

# 如何串行执行异步任务并按顺序返回结果？

## 题目

实现 serialAll(tasks)，按顺序启动任务并返回结果数组；空数组返回空结果，任务拒绝或同步抛错时立即拒绝且不启动后续任务。

## 简要回答

传入 `() => Promise` 形式的任务函数，用 for 循环逐个调用并 await。已创建的 Promise 往往已经启动，无法通过等待顺序让底层操作重新串行。

与 Promise.all 都能按输入顺序返回结果、失败时拒绝，但输入契约和失败后的剩余任务行为也不同，不能严格声称“只有串行这一点不同”。

## 实现与示例

约定输入为函数数组，函数可返回普通值、thenable 或 Promise；本实现先校验所有元素，不支持任意 iterable，也不是 Promise.all 的完整 polyfill。

```js
async function serialAll(tasks) {
  if (!Array.isArray(tasks)) throw new TypeError('tasks must be an array');
  const queue = Array.from(tasks);
  if (queue.some(task => typeof task !== 'function')) {
    throw new TypeError('each task must be a function');
  }
  const results = [];
  for (const task of queue) results.push(await task());
  return results;
}
```

示例：`await serialAll([() => Promise.resolve(1), () => 2])` 得到 `[1, 2]`。若首项失败，第二个函数不会调用。

调度开销 O(n)，结果和输入快照空间 O(n)；等待耗时约为各任务耗时之和。单个任务永不结束会阻塞整个队列；取消需任务额外支持 AbortSignal。

## 常见问法

“串行地执行传入的 promises，实现效果与 promise.all 区别只有串行执行。”此处按可实现的延迟任务契约规范化，原题未说明的失败行为采用遇错停止。

## 相关知识点

- [Promise 聚合与异步任务调度](../../knowledge/programming-languages/k-7aa10924-async.md)

## 示例验证

在 Node 中验证空输入、普通值、thenable、串行启动、拒绝、同步抛错及非法元素；未覆盖任意 iterable 或取消功能。

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-10-frontend-and-os.md)
