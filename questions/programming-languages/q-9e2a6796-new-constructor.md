---
id: "q-9e2a6796"
title: "new MyQueue() 做了什么，this.p = [] 存在哪里？"
category: "programming-languages"
tags: ["JavaScript"]
status: "ready"
type: "principle"
created: "2026-09-22"
updated: "2026-09-22"
scope: ["普通 function 构造函数；非派生 class"]
relations:
  examines: ["k-02569c54"]
---

# new MyQueue() 做了什么，this.p = [] 存在哪里？

## 题目

解释 new MyQueue() 的主要步骤，并说明 this.p = [] 与 MyQueue.prototype.p = [] 的差别。

## 简要回答

对于普通构造函数，new 创建对象，把其内部原型关联到 MyQueue.prototype，让函数中的 this 指向该对象并执行函数；默认返回该对象。显式返回对象或函数时返回它，返回原始值则仍返回默认对象。

```js
function MyQueue() { this.p = []; }
const a = new MyQueue();
const b = new MyQueue();
a.p.push(1);
console.log(a.p, b.p); // [1] []
console.log(Object.getPrototypeOf(a) === MyQueue.prototype); // true
```

this.p 是实例自己的属性，每次执行都会创建新数组；若把数组放在原型上且实例没有覆盖它，多个实例读取到同一数组，修改会相互影响。共享方法放原型上通常合适，可变实例数据通常放实例上。

## 分析与边界

若构造器 prototype 不是对象，普通构造过程会回退到相应内建原型；箭头函数不能 new。原始输入中的四步是常规解释，需补充显式对象返回值这一例外。

## 相关知识点

- [函数调用、this 绑定与构造语义](../../knowledge/programming-languages/k-02569c54-function-this-new.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-22-frontend-network-engineering.md)

