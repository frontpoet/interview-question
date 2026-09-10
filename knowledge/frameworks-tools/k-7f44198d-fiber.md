---
id: "k-7f44198d"
title: "React Element 与 Fiber"
category: "frameworks-tools"
tags: ["React"]
status: "ready"
created: "2026-09-10"
updated: "2026-09-10"
aliases: []
scope: ["React Fiber 架构概念；内部字段不是稳定 API"]
relations:
  prerequisite: ["k-d6c4eca4"]
---

# React Element 与 Fiber

## 核心概念

React Element 描述界面，Fiber 保存协调过程中的工作和状态。两者都不能简单等同于真实 DOM 节点。

## 原理与机制

Fiber 通过父子兄弟链接组织工作，保存类型、key、状态、更新队列、优先级和副作用标记；current 与 work-in-progress 支持准备新结果。调度在可让出的工作边界切分 render，commit 应用已完成的结果。

## 适用边界与易错点

并发渲染不代表多线程执行组件，也不能抢占任意长函数内部。协调使用启发式复用，不求通用树编辑的全局最优解。稳定 key 表达同层身份，数组索引在重排时可能错配状态。

## 参考资料

- [React：状态与位置、key](https://react.dev/learn/preserving-and-resetting-state)
- [React 源码：Fiber 结构（main，可能变化）](https://github.com/react/react/blob/main/packages/react-reconciler/src/ReactFiber.js)
- [React 源码：工作循环（main，可能变化）](https://github.com/react/react/blob/main/packages/react-reconciler/src/ReactFiberWorkLoop.js)

## 前置知识

- [React 更新、协调与提交](k-d6c4eca4-react-render.md)

## 关联题目

- [虚拟 DOM 的原理是什么，为什么需要 key？](../../questions/frameworks-tools/q-af53944d-virtual-dom.md)
- [React Fiber 如何支持可中断渲染？](../../questions/frameworks-tools/q-cafcea45-fiber-principle.md)
