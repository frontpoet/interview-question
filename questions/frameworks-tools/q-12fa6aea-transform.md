---
id: "q-12fa6aea"
title: "transform 有哪些作用，是否影响布局？"
category: "frameworks-tools"
tags: ["CSS"]
status: "ready"
type: "concept"
created: "2026-09-10"
updated: "2026-09-10"
scope: ["浏览器 CSS 连续媒体布局"]
relations:
  examines: ["k-edd03b5f","k-fe0ffd0f"]
---

# transform 有哪些作用，是否影响布局？

## 题目

说明平移、缩放、旋转、组合顺序和布局影响。

## 简要回答

transform 支持 translate、scale、rotate、skew 等二维或三维变换，可通过 transform-origin 改变参照原点。组合顺序会改变结果。

它通常改变视觉位置而保留普通流中的占位，可影响溢出区域，并在非 none 时建立层叠上下文及某些定位后代的包含块。动画常可利用合成优化，但应实际测量，不能认为 transform 必定“零重绘、零成本”。

## 相关知识点

- [CSS 变换、过渡与动画](../../knowledge/frameworks-tools/k-edd03b5f-motion.md)
- [CSS 定位与包含块](../../knowledge/frameworks-tools/k-fe0ffd0f-position.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-10-frontend-and-os.md)
