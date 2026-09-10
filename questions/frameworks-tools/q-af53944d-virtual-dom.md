---
id: "q-af53944d"
title: "虚拟 DOM 的原理是什么，为什么需要 key？"
category: "frameworks-tools"
tags: ["React"]
status: "ready"
type: "principle"
created: "2026-09-10"
updated: "2026-09-10"
scope: ["React Fiber 架构概念；内部字段不是稳定 API","React 18/19 客户端函数组件"]
relations:
  examines: ["k-7f44198d","k-d6c4eca4"]
---

# 虚拟 DOM 的原理是什么，为什么需要 key？

## 题目

说明界面描述、协调、真实 DOM 修改与列表身份。

## 简要回答

虚拟 DOM 通常指用内存对象描述目标界面。React 元素描述类型、props 和 key；协调根据新描述与现有树判断复用、插入、删除或更新，提交阶段操作宿主 DOM。

相同位置与类型通常保留状态，key 帮助区分同层兄弟身份；修改 key 可触发重建。列表会重排时，不应以数组索引代表稳定身份。

虚拟 DOM 提供声明式组织与协调能力，不保证比手写 DOM 操作快，也不是每次完整替换页面，更不保证找到数学上的最少 DOM 操作。

## 相关知识点

- [React Element 与 Fiber](../../knowledge/frameworks-tools/k-7f44198d-fiber.md)
- [React 更新、协调与提交](../../knowledge/frameworks-tools/k-d6c4eca4-react-render.md)

## 追问题目

- [React Fiber 如何支持可中断渲染？](q-cafcea45-fiber-principle.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-10-frontend-and-os.md)
