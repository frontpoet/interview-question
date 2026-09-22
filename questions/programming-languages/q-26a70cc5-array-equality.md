---
id: "q-26a70cc5"
title: "== 与 === 有何区别，两个 [0] 的比较结果是什么？"
category: "programming-languages"
tags: ["JavaScript"]
status: "ready"
type: "comparison"
created: "2026-09-22"
updated: "2026-09-22"
relations:
  examines: ["k-2b41b515"]
---

# == 与 === 有何区别，两个 [0] 的比较结果是什么？

## 题目

解释 == 与 === 的区别，给出 [0] == [0] 和 [0] === [0] 的结果。

## 简要回答

结果均为 false：每个数组字面量创建一个新对象，两边不是同一引用。== 只在特定异类型组合下执行转换，不会因为数组内容相同就做深比较；=== 不做跨类型隐式转换。

## 示例

```js
const a = [0];
console.log([0] == [0], [0] === [0]); // false false
console.log(a == a, a === a);         // true true
console.log([0] == 0, [0] === 0);     // true false
console.log(null == undefined);      // true
```

需要比较数组内容，应明确长度、顺序、元素类型及嵌套对象规则，再实现相应比较；JSON.stringify 不是通用深相等方案。

## 相关知识点

- [JavaScript 相等比较与类型转换](../../knowledge/programming-languages/k-2b41b515-equality-coercion.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-22-frontend-network-engineering.md)

