---
id: "q-a15bc115"
title: "TypeScript 的 any 和 unknown 有什么区别？"
category: "programming-languages"
tags: ["TypeScript"]
status: "ready"
type: "comparison"
created: "2026-09-22"
updated: "2026-09-22"
scope: ["TypeScript 4.9+；strict 模式"]
relations:
  examines: ["k-53edaabc"]
---

# TypeScript 的 any 和 unknown 有什么区别？

## 题目

比较 any 和 unknown 的赋值、属性访问和使用场景。

## 简要回答

二者都能接收任意类型的值；any 基本放弃静态检查，可以直接访问属性或调用；unknown 要先收窄，适合外部不可信或结构未确定的数据。any 可用于逐步迁移的局部边界，但应避免扩散。

## 示例

```ts
function readName(value: unknown): string {
  if (typeof value === 'object' && value !== null &&
      'name' in value && typeof value.name === 'string') {
    return value.name;
  }
  throw new TypeError('name must be a string');
}
```

这里真实检查了输入。写成 `(value as { name: string }).name` 不会产生运行时校验。示例按 TypeScript 4.9+ 的 in 属性收窄编写。

## 相关知识点

- [any、unknown 与类型收窄](../../knowledge/programming-languages/k-53edaabc-any-unknown.md)

## 示例验证

使用 TypeScript 5.8.3 strict/noEmit 检查本页代码，同时检查 unknown 的受限访问/赋值及 any 不能赋给 never；编译后的 readName 在 Node 中覆盖合法值、null、非对象、缺少属性和属性类型错误。

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-22-frontend-network-engineering.md)
