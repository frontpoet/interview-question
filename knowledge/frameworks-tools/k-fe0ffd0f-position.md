---
id: "k-fe0ffd0f"
title: "CSS 定位与包含块"
category: "frameworks-tools"
tags: ["CSS"]
status: "ready"
created: "2026-09-10"
updated: "2026-09-10"
aliases: []
scope: ["浏览器 CSS 连续媒体布局"]
relations:
  prerequisite: ["k-7e045f7e"]
---

# CSS 定位与包含块

## 核心概念

position 决定定位方式；包含块提供尺寸或定位偏移的参照。包含块不一定是直接父元素。

## 原理与机制

relative 从正常位置偏移并保留占位。absolute 脱离普通流，按其包含块定位。fixed 通常按视口定位，但 transform 等属性可使祖先建立固定定位包含块。sticky 保留占位，在最近滚动容器的滚动视口中按 inset 约束偏移，并受自身包含块边界限制。

## 适用边界与易错点

sticky 对应轴需要非 auto 的 inset，并需要可滚动和可移动空间；检查祖先 overflow、容器高度与拉伸行为。层叠上下文决定绘制层级，不能仅靠不断增大 z-index 跨越祖先层级。

## 参考资料

- [MDN：position](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/position)
- [MDN：transform](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/transform)

## 前置知识

- [CSS 盒模型与布局](k-7e045f7e-css-layout.md)

## 关联题目

- [CSS 常用属性有哪些，分别解决什么问题？](../../questions/frameworks-tools/q-82f696ce-css-properties.md)
- [position 有哪些值，如何选择？](../../questions/frameworks-tools/q-4ec68f7a-position-values.md)
- [absolute 与 fixed 有什么区别？](../../questions/frameworks-tools/q-60dc83c6-absolute-fixed.md)
- [fixed 与 sticky 有什么区别，sticky 为什么可能不生效？](../../questions/frameworks-tools/q-a67dce12-fixed-sticky.md)
- [relative 相对于谁定位，left 是否生效？](../../questions/frameworks-tools/q-62312ffd-relative-offset.md)
- [如何用 CSS 实现元素水平和垂直居中？](../../questions/frameworks-tools/q-5da460ce-centering.md)
- [transform 有哪些作用，是否影响布局？](../../questions/frameworks-tools/q-12fa6aea-transform.md)
