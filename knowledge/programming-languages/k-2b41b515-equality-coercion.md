---
id: "k-2b41b515"
title: "JavaScript 相等比较与类型转换"
category: "programming-languages"
tags: ["JavaScript"]
status: "ready"
created: "2026-09-22"
updated: "2026-09-22"
---

# JavaScript 相等比较与类型转换

## 核心概念

严格相等 === 不执行跨类型转换；宽松相等 == 按规范对特定类型组合进行转换。两者比较两个对象时均按对象身份，而非递归比较内容。

## 原理与机制

两个独立数组是两个对象，所以 [0] == [0] 和 [0] === [0] 都是 false。同一引用 const a = [0] 则 a == a 和 a === a 都为 true。对象与原始值进行 == 比较时可能先转换为原始值，所以 [0] == 0 为 true，而 [0] === 0 为 false。null == undefined 为 true。

## 适用边界与易错点

NaN === NaN 为 false，+0 === -0 为 true；Object.is 的这两种结果不同。== 不是“把双方一律转成数字”，也不对两个对象执行值转换。日常优先用 ===；有意用 x == null 同时判断 null/undefined 时，应理解浏览器 document.all 的历史例外。

## 参考资料

- [MDN：Equality](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Equality)

## 关联题目

- [== 与 === 有何区别，两个 [0] 的比较结果是什么？](../../questions/programming-languages/q-26a70cc5-array-equality.md)

