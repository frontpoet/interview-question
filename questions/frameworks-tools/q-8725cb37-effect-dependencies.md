---
id: "q-8725cb37"
title: "Hooks 依赖数组如何比较，怎样避免无意义重跑？"
category: "frameworks-tools"
tags: ["React","Hooks"]
status: "ready"
type: "principle"
created: "2026-09-10"
updated: "2026-09-10"
scope: ["React Hooks；固定长度的依赖数组","React 18/19 客户端 Effects；开发 StrictMode 可能重放"]
relations:
  examines: ["k-2777a264","k-486fa8e9"]
---

# Hooks 依赖数组如何比较，怎样避免无意义重跑？

## 题目

解释依赖数组与组件更新的关系，以及对象、函数依赖的处理。

## 简要回答

React 对每个位置使用 Object.is 比较：原始值按该算法判断，对象和函数按引用判断。它与 === 并非完全相同，例如 Object.is(NaN, NaN) 为 true，Object.is(+0, -0) 为 false。

useEffect 不传依赖时每次提交后重跑；空数组没有响应式依赖；传数组时依赖变化才重跑，挂载和开发重放另算。依赖变化决定 Effect 或缓存行为，不是单独触发组件渲染的机制。

只在内容确实未变时保留原引用；数据变更必须不可变更新，不能原地修改对象后返回它。对象可在 Effect 内创建，依赖改为必要原始值；确有需要再使用 useMemo/useCallback，不靠删除依赖掩盖问题。

## 分析与边界

每次创建内容相同的新对象，引用已不同，会使对应比较失败；只有 Effect 自身完全不必重跑时，才称为无意义重跑。依赖数组长度和顺序应固定，遵守 exhaustive-deps。

## 相关知识点

- [React 依赖比较与引用稳定性](../../knowledge/frameworks-tools/k-2777a264-identity.md)
- [React Effect 生命周期](../../knowledge/frameworks-tools/k-486fa8e9-effects.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-10-frontend-and-os.md)
