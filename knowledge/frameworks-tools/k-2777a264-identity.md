---
id: "k-2777a264"
title: "React 依赖比较与引用稳定性"
category: "frameworks-tools"
tags: ["React","Hooks"]
status: "ready"
created: "2026-09-10"
updated: "2026-09-10"
aliases: ["依赖数组","引用稳定性"]
scope: ["React Hooks；固定长度的依赖数组"]
---

# React 依赖比较与引用稳定性

## 核心概念

Hooks 按位置用 Object.is 比较依赖，比较对象和函数时看引用，不做深比较。

## 原理与机制

useMemo 缓存计算结果，useCallback 缓存函数引用。需要稳定引用时先减少无意义对象创建，再针对昂贵计算或 memo 子组件使用缓存。依赖必须完整包含被读取的响应式值。

## 适用边界与易错点

依赖改变影响 Effect 重跑或缓存失效，不直接等于触发组件渲染。数据未变可保留引用；数据变更应创建新对象，禁止原地修改 state。Object.is 与 === 在 NaN 和正负零上不同。缓存是优化，不是业务正确性保证。

## 参考资料

- [React：useMemo](https://react.dev/reference/react/useMemo)
- [React：useCallback](https://react.dev/reference/react/useCallback)
- [React：不可变对象更新](https://react.dev/learn/updating-objects-in-state)

## 关联题目

- [Hooks 依赖数组如何比较，怎样避免无意义重跑？](../../questions/frameworks-tools/q-8725cb37-effect-dependencies.md)
- [如何实现跳过初始挂载的 useUpdateEffect？](../../questions/frameworks-tools/q-70a359bf-skip-initial-effect.md)
- [useMemo 和 useCallback 有什么区别，何时使用？](../../questions/frameworks-tools/q-d8cd67e7-memo-callback.md)
