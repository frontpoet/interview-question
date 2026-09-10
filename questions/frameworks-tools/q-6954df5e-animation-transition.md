---
id: "q-6954df5e"
title: "animation 与 transition 有什么区别？"
category: "frameworks-tools"
tags: ["CSS"]
status: "ready"
type: "comparison"
created: "2026-09-10"
updated: "2026-09-10"
relations:
  examines: ["k-edd03b5f"]
---

# animation 与 transition 有什么区别？

## 题目

比较触发方式、过程控制和适用场景。

## 简要回答

transition 在属性值改变时描述两种状态之间的过渡，适合 hover、展开收起等状态变化。animation 使用 keyframes 定义多阶段过程，可控制循环次数、方向和播放状态，适合持续或复杂动作。

二者都可改变 transform 等可动画属性，也都涉及时长、延迟和缓动。animation 本身不保证性能更好，成本取决于变化属性和实际渲染工作。

## 相关知识点

- [CSS 变换、过渡与动画](../../knowledge/frameworks-tools/k-edd03b5f-motion.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-10-frontend-and-os.md)
