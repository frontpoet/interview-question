---
id: "q-a67dce12"
title: "fixed 与 sticky 有什么区别，sticky 为什么可能不生效？"
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

# fixed 与 sticky 有什么区别，sticky 为什么可能不生效？

## 题目

比较 fixed 与 sticky，并说明粘性定位的必要条件。

## 简要回答

fixed 脱离普通流，通常一直固定在视口；sticky 保留原位置占位，滚动到指定阈值后发生粘性偏移，且不能越过自身包含块边界。

sticky 不生效时检查对应轴的 top/bottom 等是否为非 auto、实际滚动祖先是否符合预期、父容器是否有足够空间、Flex/Grid 拉伸是否使元素无移动空间。祖先 overflow 可能改变所参照的滚动容器。

## 相关知识点

- [CSS 定位与包含块](../../knowledge/frameworks-tools/k-fe0ffd0f-position.md)

## 原题目

- [position 有哪些值，如何选择？](q-4ec68f7a-position-values.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-10-frontend-and-os.md)
