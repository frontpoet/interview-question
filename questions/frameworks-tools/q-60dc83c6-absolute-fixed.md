---
id: "q-60dc83c6"
title: "absolute 与 fixed 有什么区别？"
category: "frameworks-tools"
tags: ["CSS"]
status: "ready"
type: "comparison"
created: "2026-09-10"
updated: "2026-09-10"
scope: ["浏览器 CSS 连续媒体布局"]
relations:
  examines: ["k-fe0ffd0f"]
  follow_up_to: ["q-4ec68f7a"]
---

# absolute 与 fixed 有什么区别？

## 题目

比较定位参照、滚动行为和使用场景。

## 简要回答

两者都脱离普通流。absolute 按绝对定位包含块定位，常用于容器角标或浮层；fixed 通常按视口定位，常用于固定工具栏。

absolute 通常随所在内容滚动；fixed 在按视口定位时不随文档滚动。祖先 transform 等属性可能改变 fixed 的包含块，因此“fixed 永远相对浏览器窗口”不准确。

## 相关知识点

- [CSS 定位与包含块](../../knowledge/frameworks-tools/k-fe0ffd0f-position.md)

## 原题目

- [position 有哪些值，如何选择？](q-4ec68f7a-position-values.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-10-frontend-and-os.md)
