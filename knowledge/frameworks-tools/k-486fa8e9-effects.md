---
id: "k-486fa8e9"
title: "React Effect 生命周期"
category: "frameworks-tools"
tags: ["React","Hooks"]
status: "ready"
created: "2026-09-10"
updated: "2026-09-10"
aliases: ["Effect 生命周期"]
scope: ["React 18/19 客户端 Effects；开发 StrictMode 可能重放"]
relations:
  prerequisite: ["k-d6c4eca4"]
---

# React Effect 生命周期

## 核心概念

Effect 用于把组件与外部系统同步。一次同步由 setup 和对应 cleanup 组成。

## 原理与机制

依赖变化时先清理旧同步再建立新同步，卸载时清理。Layout Effect 在提交后的绘制前执行，可用于尺寸测量和同步定位；普通 Effect 通常较晚执行，但不保证在绘制之后。

## 适用边界与易错点

开发环境可能额外 setup/cleanup，逻辑应能恢复。Effect 不在服务端渲染中运行。Layout Effect 阻塞绘制，应保持短小；网络订阅等通常用普通 Effect。

## 参考资料

- [React：useEffect](https://react.dev/reference/react/useEffect)
- [React：useLayoutEffect](https://react.dev/reference/react/useLayoutEffect)
- [React：StrictMode](https://react.dev/reference/react/StrictMode)

## 前置知识

- [React 更新、协调与提交](k-d6c4eca4-react-render.md)

## 关联题目

- [React 组件从 setState 到显示更新经历哪些步骤？](../../questions/frameworks-tools/q-d2f67a35-react-update.md)
- [useEffect 和 useLayoutEffect 有什么区别？](../../questions/frameworks-tools/q-bf24550f-effect-layout.md)
- [Hooks 依赖数组如何比较，怎样避免无意义重跑？](../../questions/frameworks-tools/q-8725cb37-effect-dependencies.md)
- [如何实现跳过初始挂载的 useUpdateEffect？](../../questions/frameworks-tools/q-70a359bf-skip-initial-effect.md)
- [React 19 有哪些值得关注的新能力？](../../questions/frameworks-tools/q-be806d53-react-19-features.md)
