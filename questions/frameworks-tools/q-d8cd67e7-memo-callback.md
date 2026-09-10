---
id: "q-d8cd67e7"
title: "useMemo 和 useCallback 有什么区别，何时使用？"
category: "frameworks-tools"
tags: ["React","Hooks"]
status: "ready"
type: "comparison"
created: "2026-09-10"
updated: "2026-09-10"
scope: ["React Hooks；固定长度的依赖数组"]
relations:
  examines: ["k-2777a264"]
---

# useMemo 和 useCallback 有什么区别，何时使用？

## 题目

比较缓存对象、触发条件、用途和成本。

## 简要回答

useMemo 缓存计算结果：`useMemo(() => calculate(data), [data])`；useCallback 缓存函数引用：`useCallback(() => submit(id), [id])`，不会执行该回调。

依赖按 Object.is 比较。昂贵计算可用 useMemo；传给 memo 子组件或需要稳定订阅依赖的函数可考虑 useCallback。子组件仍可能因自身 state、Context 或其他 prop 改变而更新。

缓存也有比较、内存和可读性成本。先测量并减少不必要的 Effect、对象依赖，不能把缓存用于保证副作用只执行一次或存放必须持久的状态。

## 相关知识点

- [React 依赖比较与引用稳定性](../../knowledge/frameworks-tools/k-2777a264-identity.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-10-frontend-and-os.md)
