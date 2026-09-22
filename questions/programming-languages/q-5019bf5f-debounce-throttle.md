---
id: "q-5019bf5f"
title: "节流和防抖有什么区别，如何实现？"
category: "programming-languages"
tags: ["JavaScript","性能"]
status: "ready"
type: "coding"
created: "2026-09-22"
updated: "2026-09-22"
scope: ["仅尾触发 debounce；仅首触发 throttle；ES2015+"]
relations:
  examines: ["k-57abeb7a"]
---

# 节流和防抖有什么区别，如何实现？

## 题目

解释防抖与节流，给出保留 this、参数并支持取消的简化实现。

## 简要回答

防抖适合输入停顿后再搜索；节流适合连续事件中限制执行频率。以下分别实现“仅尾触发防抖”和“仅首触发节流”，不包含首尾组合、maxWait 和 flush；返回的包装函数不返回业务结果。

## 实现与示例

输入 fn 为函数，wait 为 0～2147483647 的整数毫秒；输出可调用函数及 cancel 方法。代码使用 ES2015+，定时器环境需提供 setTimeout/clearTimeout。

```js
function checkTiming(fn, wait) {
  if (typeof fn !== 'function') throw new TypeError('fn must be a function');
  if (!Number.isInteger(wait) || wait < 0 || wait > 2147483647)
    throw new RangeError('invalid wait');
}
function debounce(fn, wait) {
  checkTiming(fn, wait);
  let timer = null;
  function wrapped(...args) {
    if (timer !== null) clearTimeout(timer);
    timer = setTimeout(() => {
      timer = null;
      fn.apply(this, args);
    }, wait);
  }
  wrapped.cancel = () => {
    if (timer !== null) clearTimeout(timer);
    timer = null;
  };
  return wrapped;
}
function throttle(fn, wait) {
  checkTiming(fn, wait);
  let timer = null;
  function wrapped(...args) {
    if (timer !== null) return;
    // 先占窗口，避免 fn 内重入绕过限制。
    timer = setTimeout(() => { timer = null; }, wait);
    fn.apply(this, args);
  }
  wrapped.cancel = () => {
    if (timer !== null) clearTimeout(timer);
    timer = null;
  };
  return wrapped;
}
```

若 wait = 100，依次在 0、30、60ms 调用：防抖在约 160ms 使用第三次参数执行；节流仅在 0ms 使用第一次参数执行。若再于 180ms 调用，节流立即再次执行；防抖重新安排在约 280ms。

## 复杂度与边界

每次调度操作 O(1)，每个包装函数至多一个定时器，额外保存最近参数的空间 O(m)，m 为参数数。同步回调异常不被吞掉，异步返回值不自动处理；wait = 0 也遵循事件循环。取消后防抖不再执行待处理回调，节流立即解除冷却。若要求最后状态必达，应扩展节流尾触发策略。

## 相关知识点

- [防抖与节流的时间语义](../../knowledge/programming-languages/k-57abeb7a-debounce-throttle.md)

## 示例验证

在 Node.js 22.16.0 中使用确定性模拟时钟，验证最新参数、this、取消、零延迟、首触发冷却、重入和异常传播；未验证浏览器后台定时器节流或真实输入事件集成。

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-22-frontend-network-engineering.md)
