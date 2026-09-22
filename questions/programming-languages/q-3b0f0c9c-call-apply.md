---
id: "q-3b0f0c9c"
title: "如何手写 call 和 apply，临时属性法有哪些限制？"
category: "programming-languages"
tags: ["JavaScript"]
status: "ready"
type: "coding"
created: "2026-09-22"
updated: "2026-09-22"
scope: ["明确受限的教学实现，非 ECMAScript 完整 polyfill"]
relations:
  examines: ["k-02569c54"]
---

# 如何手写 call 和 apply，临时属性法有哪些限制？

## 题目

手写 call/apply 的教学版本，解释二者参数形式，并说明为什么不能冒充完整 polyfill。

## 简要回答

call 逐个传参数，apply 接收类数组参数；二者立即执行并返回结果。临时属性法通过 `receiver[key](...args)` 让函数作为对象方法调用，使用 Symbol 避免覆盖普通属性，用 finally 清理。

## 约束与实现

本题限制为可扩展的普通对象接收者、不含 Proxy 的对象、可调用函数；apply 只接受数组或 null/undefined。不修改 Function.prototype。禁止传入 null、原始值或不可扩展接收者；省略原生 apply 对任意类数组的支持。现代 JavaScript。

```js
function myCall(fn, receiver, ...args) {
  if (typeof fn !== 'function') throw new TypeError('fn must be callable');
  if (receiver === null ||
      (typeof receiver !== 'object' && typeof receiver !== 'function') ||
      !Object.isExtensible(receiver)) {
    throw new TypeError('receiver must be an extensible object');
  }
  const key = Symbol('temporaryCall');
  Object.defineProperty(receiver, key, { value: fn, configurable: true });
  try {
    return receiver[key](...args);
  } finally {
    delete receiver[key];
  }
}
function myApply(fn, receiver, args) {
  if (args == null) args = [];
  if (!Array.isArray(args)) throw new TypeError('args must be an array');
  return myCall(fn, receiver, ...args);
}
```

示例：`myApply(function(a, b) { return this.base + a + b; }, { base: 10 }, [1, 2])` 返回 13。

## 分析与边界

原生 call/apply 可以把 null、undefined、原始值传给严格函数；非严格函数会自行替换或装箱 this，临时属性法无法通用地模拟两种行为。用 Object(receiver) 和 globalThis 强行转换只覆盖部分非严格模式场景。箭头函数始终使用词法 this。真实工程应使用原生 call/apply 或 Reflect.apply。

## 复杂度与边界情况

传递 n 个参数的展开成本 O(n)，额外参数空间 O(n)，临时属性 O(1)，不含被调用函数自身开销。验证返回值、参数顺序、异常清理及非法接收者；大量参数仍可能超过引擎调用限制。

## 相关知识点

- [函数调用、this 绑定与构造语义](../../knowledge/programming-languages/k-02569c54-function-this-new.md)

## 示例验证

在 Node.js 22.16.0 中验证返回值、参数顺序、空参数、异常后的临时属性清理及非法输入；未宣称支持范围外的原生调用语义。

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-22-frontend-network-engineering.md)
