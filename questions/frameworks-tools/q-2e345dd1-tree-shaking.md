---
id: "q-2e345dd1"
title: "为什么具名 import 有时只打包用到的代码？"
category: "frameworks-tools"
tags: ["JavaScript","构建"]
status: "ready"
type: "principle"
created: "2026-09-10"
updated: "2026-09-10"
scope: ["以支持 ESM Tree Shaking 的生产构建为例"]
relations:
  examines: ["k-71d21222"]
---

# 为什么具名 import 有时只打包用到的代码？

## 题目

解释“import 一个东西只打包一个东西”的条件及例外。

## 简要回答

这通常依赖 Tree Shaking：构建器分析静态导入导出，移除未使用且无必要副作用的代码。生产优化、模块格式和包的 sideEffects 声明都会影响结果。

具名 import 不等于精确打包一个符号；被引用的内部依赖和模块初始化可能留下。按需入口、代码分割和 Tree Shaking 也不是同一机制。应检查生产产物或 bundle 分析报告，而非仅凭 import 写法判断。

## 相关知识点

- [Tree Shaking 与模块副作用](../../knowledge/frameworks-tools/k-71d21222-tree.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-10-frontend-and-os.md)
