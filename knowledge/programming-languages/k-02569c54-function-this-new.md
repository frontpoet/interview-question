---
id: "k-02569c54"
title: "函数调用、this 绑定与构造语义"
category: "programming-languages"
tags: ["JavaScript","TypeScript"]
status: "ready"
created: "2026-09-22"
updated: "2026-09-22"
scope: ["现代 JavaScript；TypeScript 不改变 运行时规则"]
---

# 函数调用、this 绑定与构造语义

## 核心概念

普通函数的 this 由调用方式决定；箭头函数沿词法作用域读取 this。构造调用与普通调用是不同内部操作，不是简单给函数指定一个 this 就能完全互换。

## 原理与机制

obj.fn() 的 this 通常为 obj；严格模式独立调用为 undefined；call/apply 立即调用并显式指定接收者；bind 返回保存接收者和前置参数的新函数。箭头函数没有自己的 this、arguments，也没有可用于 new 的构造能力。函数声明与表达式的初始化规则不同，不能把所有普通函数都说成“可以提前调用”。参见 [MDN：箭头函数](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)。

new 调用普通构造函数时创建对象、连接构造器 prototype、绑定 this 并执行函数；显式返回对象或函数会替换默认实例，返回原始值则忽略。每次在构造函数中 this.p = [] 都新建一个实例数组。class 必须通过构造调用，派生类还涉及 super，不能套用 fn.apply 模拟。参见 [MDN：new](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/new)。

## 适用边界与易错点

对象方法简写、箭头、async 函数等不一定可构造。原生 bind 的结果只有在目标可构造时才可构造，new 时忽略绑定的 this；手写包装通常不能完全复现其 prototype、instanceof、name、length 等细节。规范依据：[ECMAScript Function.prototype.bind](https://tc39.es/ecma262/multipage/fundamental-objects.html#sec-function.prototype.bind)。

## 关联题目

- [TypeScript 中箭头函数和普通函数有什么区别？](../../questions/programming-languages/q-7d15739a-arrow-ordinary-function.md)
- [new MyQueue() 做了什么，this.p = [] 存在哪里？](../../questions/programming-languages/q-9e2a6796-new-constructor.md)
- [如何手写 call 和 apply，临时属性法有哪些限制？](../../questions/programming-languages/q-3b0f0c9c-call-apply.md)
- [如何使用 call/apply 实现 bind，并处理 new？](../../questions/programming-languages/q-9b1b88a0-bind-with-apply.md)

