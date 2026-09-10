---
id: "q-62312ffd"
title: "relative 相对于谁定位，left 是否生效？"
category: "frameworks-tools"
tags: ["CSS"]
status: "ready"
type: "concept"
created: "2026-09-10"
updated: "2026-09-10"
scope: ["浏览器 CSS 连续媒体布局"]
relations:
  examines: ["k-fe0ffd0f"]
  follow_up_to: ["q-4ec68f7a"]
---

# relative 相对于谁定位，left 是否生效？

## 题目

解释 `position: relative; left: 20px` 的效果。

## 简要回答

相对于元素在正常布局中的位置向右偏移 20px，原占位保留，其他元素不会为此重新让出空间。它不是相对于父元素左边缘定位。

relative 还可为 absolute 后代建立定位包含块。偏移可能造成覆盖或溢出，不能用它替代正常布局间距。

## 相关知识点

- [CSS 定位与包含块](../../knowledge/frameworks-tools/k-fe0ffd0f-position.md)

## 原题目

- [position 有哪些值，如何选择？](q-4ec68f7a-position-values.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-10-frontend-and-os.md)
