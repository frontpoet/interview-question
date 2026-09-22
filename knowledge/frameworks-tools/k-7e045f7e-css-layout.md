---
id: "k-7e045f7e"
title: "CSS 盒模型与布局"
category: "frameworks-tools"
tags: ["CSS"]
status: "ready"
created: "2026-09-10"
updated: "2026-09-22"
aliases: []
scope: ["浏览器 CSS；默认横向书写模式"]
---

# CSS 盒模型与布局

## 核心概念

元素生成的盒由内容、内边距、边框和外边距组成。布局决定盒的尺寸和相互位置。

## 原理与机制

`content-box` 的 width 不包含 padding 和 border；`border-box` 包含两者，均不包含 margin。`display` 同时决定外部参与布局的方式和内部布局方式，例如 `inline-flex` 外部行内、内部 Flex。

Flex 按主轴和交叉轴分配空间，Grid 按行列组织轨道。居中先确认居中对象、轴向和容器可用空间。

### 尺寸计算

普通块盒设置 width: 200px、左右 padding 各 10px、左右 border 各 2px 时，content-box 的边框盒宽 224px；border-box 的边框盒宽 200px、内容宽 176px，两种都不包含 margin。border-box 的内容尺寸不会被压成负值：若边框和内边距本身超过指定尺寸，边框盒仍可能更大。

box-sizing 默认不继承，可用通配选择器连同伪元素显式设为 border-box；Flex/Grid 分配、min/max 约束和普通行内元素规则仍会影响最终尺寸。

## 适用边界与易错点

`text-align` 对齐行内内容，不直接移动块盒；普通行内盒的 width/height 与块盒不同。`display: none` 不生成盒，`visibility: hidden` 通常保留布局位置。

## 参考资料

- [MDN：盒模型](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Box_model/Introduction)
- [MDN：display](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/display)

## 关联题目

- [CSS 常用属性有哪些，分别解决什么问题？](../../questions/frameworks-tools/q-82f696ce-css-properties.md)
- [display 如何影响元素的外部布局和内部布局？](../../questions/frameworks-tools/q-ce38d22b-display.md)
- [如何用 CSS 实现元素水平和垂直居中？](../../questions/frameworks-tools/q-5da460ce-centering.md)
- [什么是 CSS 盒模型，box-sizing 如何影响尺寸？](../../questions/frameworks-tools/q-a9e0dcb1-box-sizing.md)
