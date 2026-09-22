---
id: "q-7d15739a"
title: "TypeScript 中箭头函数和普通函数有什么区别？"
category: "programming-languages"
tags: ["JavaScript","TypeScript"]
status: "ready"
type: "comparison"
created: "2026-09-22"
updated: "2026-09-22"
relations:
  examines: ["k-02569c54"]
---

# TypeScript 中箭头函数和普通函数有什么区别？

## 题目

比较 TypeScript 中箭头函数与普通函数，说明 this、arguments、构造调用与类型声明的差异。

## 简要回答

| 维度 | 箭头函数 | 普通 function 函数 |
| --- | --- | --- |
| this | 捕获外层 this，call/apply/bind 不能改写它 | 由调用方式决定 |
| arguments | 无自身 arguments，通常用 rest 参数 | 有自身 arguments |
| new | 不可构造 | 普通非 async、非 generator 的 function 通常可构造 |
| 定义 | 表达式；常赋给 const/let | 可声明或表达式，提升行为取决于形式 |
| TS 标注 | 可写参数、返回值、泛型 | 也可写这些类型，并可声明显式 this 参数 |

## 分析与边界

这些运行时差异来自 JavaScript，TS 主要补充静态检查。对象方法若需动态接收者，使用普通方法；类字段箭头函数适合保留实例 this，但每个实例创建自己的函数。不要把箭头函数简单说成“匿名函数”或“性能更好”。函数声明支持重载声明；箭头函数也能被赋给具有多个调用签名的类型，不能说它完全不支持重载类型。

## 参考资料

- [TypeScript：函数与 this 参数](https://www.typescriptlang.org/docs/handbook/2/functions.html)

## 相关知识点

- [函数调用、this 绑定与构造语义](../../knowledge/programming-languages/k-02569c54-function-this-new.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-22-frontend-network-engineering.md)

