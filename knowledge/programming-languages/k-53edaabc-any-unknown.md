---
id: "k-53edaabc"
title: "any、unknown 与类型收窄"
category: "programming-languages"
tags: ["TypeScript"]
status: "ready"
created: "2026-09-22"
updated: "2026-09-22"
---

# any、unknown 与类型收窄

## 核心概念

any 允许绕过大量类型检查；unknown 表示值可以来自任何类型，但使用时必须先证明符合需要的类型。它们都不是运行时数据验证。

## 原理与机制

任意值可赋给 unknown 或 any。any 可直接访问属性、调用并向多数类型赋值，容易继续传播；unknown 只能直接赋给 unknown/any，需用 typeof、instanceof、属性检查或类型守卫收窄后再使用。any 也不能说成“可赋给所有类型”，例如赋给 never 仍会报错。unknown 的联合通常吸收其他类型，交叉通常保留另一类型；any 有特殊规则，不宜按普通集合推理。

## 适用边界与易错点

接口返回值、消息输入和 catch 值优先保留未知性，在边界解析。as User 只改变编译器认知，不会校验输入；typeof value === 'object' 后还要排除 null。类型谓词的正确性仍由实现负责。

## 参考资料

- [TypeScript 3.0：unknown 顶层类型](https://www.typescriptlang.org/docs/handbook/release-notes/typescript-3-0.html)

## 关联题目

- [TypeScript 的 any 和 unknown 有什么区别？](../../questions/programming-languages/q-a15bc115-any-vs-unknown.md)

