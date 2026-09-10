---
id: "k-d6c4eca4"
title: "React 更新、协调与提交"
category: "frameworks-tools"
tags: ["React"]
status: "ready"
created: "2026-09-10"
updated: "2026-09-10"
aliases: ["React 更新流程","Reconciliation"]
scope: ["React 18/19 客户端函数组件"]
---

# React 更新、协调与提交

## 核心概念

更新触发新一轮渲染；协调决定复用与修改；提交将结果应用到宿主环境。协调属于 render 工作，不是之后独立的一次全树 diff。

## 原理与机制

setState 将更新入队，当前函数中的 state 保持本次渲染快照。React 按优先级处理更新，调用组件得到元素描述，依据类型、key 和位置复用节点。Render 可被暂停或放弃，Commit 应用宿主修改并处理相关生命周期。

## 适用边界与易错点

一次 render 未必导致 DOM 变化。批处理不等于所有更新永远只提交一次。真实 DOM 完成更新后，浏览器仍需执行自己的渲染步骤。

## 参考资料

- [React：Render and Commit](https://react.dev/learn/render-and-commit)
- [React：更新队列](https://react.dev/learn/queueing-a-series-of-state-updates)

## 关联题目

- [React 组件从 setState 到显示更新经历哪些步骤？](../../questions/frameworks-tools/q-d2f67a35-react-update.md)
- [虚拟 DOM 的原理是什么，为什么需要 key？](../../questions/frameworks-tools/q-af53944d-virtual-dom.md)
