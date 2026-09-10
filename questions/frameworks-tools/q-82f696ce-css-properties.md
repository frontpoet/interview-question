---
id: "q-82f696ce"
title: "CSS 常用属性有哪些，分别解决什么问题？"
category: "frameworks-tools"
tags: ["CSS"]
status: "ready"
type: "concept"
created: "2026-09-10"
updated: "2026-09-10"
scope: ["浏览器 CSS；默认横向书写模式","浏览器 CSS 连续媒体布局"]
relations:
  examines: ["k-7e045f7e","k-fe0ffd0f","k-edd03b5f"]
---

# CSS 常用属性有哪些，分别解决什么问题？

## 题目

按用途介绍常用 CSS 属性，而非只背属性名。

## 简要回答

- 尺寸与盒模型：width/height、min/max-width、padding、border、margin、box-sizing。
- 布局与间距：display、flex、grid-template-columns、gap、justify-content、align-items。
- 定位与层级：position、inset/top/left、z-index；层级受层叠上下文约束。
- 文字与外观：font、line-height、text-align、color、background、border-radius、box-shadow。
- 溢出与运动：overflow、object-fit、transform、transition、animation。

具体属性是否有效取决于布局模式，例如 justify-content 的对齐方向取决于所用布局及轴向。

## 相关知识点

- [CSS 盒模型与布局](../../knowledge/frameworks-tools/k-7e045f7e-css-layout.md)
- [CSS 定位与包含块](../../knowledge/frameworks-tools/k-fe0ffd0f-position.md)
- [CSS 变换、过渡与动画](../../knowledge/frameworks-tools/k-edd03b5f-motion.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-10-frontend-and-os.md)
