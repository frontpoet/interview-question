---
id: "q-d2f67a35"
title: "React 组件从 setState 到显示更新经历哪些步骤？"
category: "frameworks-tools"
tags: ["React"]
status: "ready"
type: "principle"
created: "2026-09-10"
updated: "2026-09-10"
scope: ["React 18/19 客户端函数组件","React 18/19 客户端 Effects；开发 StrictMode 可能重放"]
relations:
  examines: ["k-d6c4eca4","k-486fa8e9","k-6e3c7224"]
---

# React 组件从 setState 到显示更新经历哪些步骤？

## 题目

以用户点击并调用状态 setter 为例，说明更新、协调、提交和绘制。

## 简要回答

1. 事件处理函数调用 setter，更新入队；当前函数内的 state 仍是本次渲染快照。
2. React 根据调度和批处理处理更新，在 Render 中调用组件，产生新的元素描述。
3. 协调是 Render 工作的一部分，按类型、key 等判断复用和变更；该过程可能被暂停或放弃。
4. Commit 应用 DOM 修改并处理相关 ref 与生命周期；不保证每次 Render 都有 DOM 修改。
5. Layout Effect 的 setup 在相关 DOM 更新后、绘制前运行；浏览器再执行必要的渲染。普通 Effect 通常较晚，但不保证总在绘制之后。

## 分析与边界

不要把 reconciliation 理解为完成全部 Render 后再单独遍历一份“新旧虚拟 DOM”做 diff。函数式更新 `setCount(c => c + 1)` 可基于队列中前一次结果计算；批处理不改变当前闭包中的 state 值。

## 相关知识点

- [React 更新、协调与提交](../../knowledge/frameworks-tools/k-d6c4eca4-react-render.md)
- [React Effect 生命周期](../../knowledge/frameworks-tools/k-486fa8e9-effects.md)
- [浏览器渲染流水线](../../knowledge/frameworks-tools/k-6e3c7224-render.md)

## 追问题目

- [useEffect 和 useLayoutEffect 有什么区别？](q-bf24550f-effect-layout.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-10-frontend-and-os.md)
