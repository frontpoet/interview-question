---
id: "q-70a359bf"
title: "如何实现跳过初始挂载的 useUpdateEffect？"
category: "frameworks-tools"
tags: ["React","Hooks"]
status: "ready"
type: "coding"
created: "2026-09-10"
updated: "2026-09-10"
scope: ["React 18/19；要求显式固定长度依赖数组；跳过初始依赖状态的挂载 setup，包括开发重放"]
relations:
  examines: ["k-486fa8e9","k-2777a264"]
---

# 如何实现跳过初始挂载的 useUpdateEffect？

## 题目

实现 useUpdateEffect(effect, deps)：初始挂载不执行业务副作用，首次依赖变化后按 Effect 生命周期执行，并支持 cleanup。

## 简要回答

仅用首次标志在第一次 setup 后改为 false，会让 StrictMode 的第二次挂载 setup 执行业务副作用。可记录上次已提交依赖，并在首次观察到依赖变化后开启业务 Effect；后续重新连接也执行 setup，以恢复被 cleanup 的订阅。

## 实现

```js
import { useEffect, useRef } from 'react';

function useUpdateEffect(effect, deps) {
  const state = useRef(null);
  useEffect(() => {
    if (state.current === null) {
      state.current = { deps: [...deps], active: false };
      return;
    }
    const changed = deps.some((value, i) => !Object.is(value, state.current.deps[i]));
    state.current.active ||= changed;
    state.current.deps = [...deps];
    if (state.current.active) return effect();
  }, deps);
}
```

示例：`useUpdateEffect(() => subscribe(roomId), [roomId])` 中，subscribe 返回退订函数。初始 roomId 不订阅，改变后订阅，下一次改变前清理，卸载时清理。一般连接场景应直接用 useEffect，这里只展示题目所需语义。

依赖数为 d，比较与快照开销 O(d)，额外空间 O(d)。空数组永不启动业务副作用；真实卸载后重新挂载会重新跳过。回调不能是返回 Promise 的 async 函数。

## 分析与边界

本实现不支持省略 deps 或动态改变其长度；它不宣称与 useEffect 的所有 API 语义完全相同。不要以定时器跳过挂载，否则会漏掉真实的早期更新。

将 useUpdateEffect 配入 eslint-plugin-react-hooks 的 additionalEffectHooks（支持该设置的版本）以检查调用处依赖；封装内部的动态 deps 需要单独审查。改变 effect 中使用的响应式值时必须列入 deps，不能靠此 Hook 绕过依赖检查。

## 参考资料

- [React：StrictMode 的 Effect 重放](https://react.dev/reference/react/StrictMode)
- [React：自定义 Effect Hook 的依赖检查](https://react.dev/reference/eslint-plugin-react-hooks/lints/exhaustive-deps)

## 相关知识点

- [React Effect 生命周期](../../knowledge/frameworks-tools/k-486fa8e9-effects.md)
- [React 依赖比较与引用稳定性](../../knowledge/frameworks-tools/k-2777a264-identity.md)

## 示例验证

使用独立 Hook 调度桩验证初始跳过、挂载 setup 重放、依赖不变、依赖变化、cleanup、重新连接及重新挂载。仓库未安装 React，尚未进行真实 React/StrictMode 集成测试。

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-10-frontend-and-os.md)
