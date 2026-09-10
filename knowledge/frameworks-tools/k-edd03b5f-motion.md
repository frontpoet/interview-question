---
id: "k-edd03b5f"
title: "CSS 变换、过渡与动画"
category: "frameworks-tools"
tags: ["CSS","性能"]
status: "ready"
created: "2026-09-10"
updated: "2026-09-10"
aliases: ["CSS 动画"]
relations:
  prerequisite: ["k-7e045f7e"]
---

# CSS 变换、过渡与动画

## 核心概念

transform 定义几何变换；transition 描述状态变化的插值过程；animation 通过关键帧定义时间序列。

## 原理与机制

transform 支持平移、旋转、缩放和倾斜，组合顺序影响结果，默认变换原点为中心。transition 指定属性、时长、缓动和延迟；animation 还能指定关键帧、循环、方向和播放状态。

## 适用边界与易错点

transform 通常不改变普通流占位，但可能影响溢出、包含块和层叠上下文。transform/opacity 动画常可减少布局和绘制工作，不保证无成本或一定进入独立合成层。尊重 prefers-reduced-motion，避免滥用 will-change。

## 参考资料

- [MDN：transform](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/transform)
- [MDN：transition](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Transitions/Using)
- [MDN：animation](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Animations/Using)

## 前置知识

- [CSS 盒模型与布局](k-7e045f7e-css-layout.md)

## 关联题目

- [CSS 常用属性有哪些，分别解决什么问题？](../../questions/frameworks-tools/q-82f696ce-css-properties.md)
- [animation 与 transition 有什么区别？](../../questions/frameworks-tools/q-6954df5e-animation-transition.md)
- [transform 有哪些作用，是否影响布局？](../../questions/frameworks-tools/q-12fa6aea-transform.md)
