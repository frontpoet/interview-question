---
id: "q-836204b0"
title: "如何实现 EventEmitter 的 on、call 和 off？"
category: "programming-languages"
tags: ["JavaScript","设计模式"]
status: "ready"
type: "coding"
created: "2026-09-22"
updated: "2026-09-22"
scope: ["自定义同步发射器；call 解释为触发事件"]
relations:
  examines: ["k-5431c10d"]
---

# 如何实现 EventEmitter 的 on、call 和 off？

## 题目

实现事件订阅 on、触发 call、取消 off；call 在本题是 emit 的别名，不是 Function.prototype.call。

## 简要回答

用 Map 保存事件列表，on 添加一条注册并返回独立取消函数；call 使用列表快照按注册顺序同步调用；off(event, fn) 移除这个函数的全部注册。触发返回本轮监听器数量，空事件返回 0。

## 约束与实现

事件名限定为字符串或 Symbol，允许重复订阅；off(event) 清空该事件。监听器 this 指向发射器；抛错立即向调用者传播。回调增删只影响下一次触发，递归触发会读取当时的新列表。不实现 once、异步等待或 Node 的特殊 error 事件。示例采用 ES2015+。

```js
class EventEmitter {
  constructor() { this.events = new Map(); }
  on(event, fn) {
    if (typeof event !== 'string' && typeof event !== 'symbol')
      throw new TypeError('invalid event');
    if (typeof fn !== 'function') throw new TypeError('listener must be a function');
    const entry = { fn };
    const list = this.events.get(event) || [];
    list.push(entry);
    this.events.set(event, list);
    return () => {
      const current = this.events.get(event);
      if (!current) return;
      const next = current.filter(item => item !== entry);
      if (next.length) this.events.set(event, next);
      else this.events.delete(event);
    };
  }
  off(event, fn) {
    if (arguments.length === 1) {
      this.events.delete(event);
      return;
    }
    const list = this.events.get(event);
    if (!list) return;
    const next = list.filter(item => item.fn !== fn);
    if (next.length) this.events.set(event, next);
    else this.events.delete(event);
  }
  call(event, ...args) {
    const snapshot = (this.events.get(event) || []).slice();
    for (const { fn } of snapshot) fn.apply(this, args);
    return snapshot.length;
  }
  emit(event, ...args) { return this.call(event, ...args); }
}
```

示例：`const bus = new EventEmitter(); const stop = bus.on('sum', (a, b) => console.log(a + b)); bus.call('sum', 1, 2); stop();` 输出 3，取消后再次触发不输出。

## 复杂度与边界

注册摊还 O(1)，取消与分发 O(n)，触发快照额外 O(n)；n 为该事件监听数，不含回调自身开销。覆盖空事件、重复订阅、Symbol 事件、触发中增删、重复取消与错误传播；组件卸载时应调用取消函数。

## 相关知识点

- [发布订阅与事件监听生命周期](../../knowledge/software-engineering/k-5431c10d-event-emitter.md)

## 示例验证

在 Node.js 22.16.0 中从本页代码块提取并执行，覆盖空事件、顺序、参数与 this、重复订阅、独立取消、Symbol、触发中增删与异常透传。不包含浏览器组件集成或异步监听器处理。

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-22-frontend-network-engineering.md)
