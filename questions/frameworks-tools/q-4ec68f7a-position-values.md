---
id: "q-4ec68f7a"
title: "position 有哪些值，如何选择？"
category: "frameworks-tools"
tags: ["CSS"]
status: "ready"
type: "concept"
created: "2026-09-10"
updated: "2026-09-10"
scope: ["浏览器 CSS 连续媒体布局"]
relations:
  examines: ["k-fe0ffd0f"]
---

# position 有哪些值，如何选择？

## 题目

说明常用定位值、占位和参照关系。

## 简要回答

| 值 | 普通流占位 | 定位方式 |
| --- | --- | --- |
| static | 保留 | 普通布局，定位 inset 不生效 |
| relative | 保留 | 从自身正常位置偏移 |
| absolute | 不保留 | 相对绝对定位包含块 |
| fixed | 不保留 | 通常相对视口，可能由祖先建立包含块 |
| sticky | 保留 | 按滚动位置调整，受滚动视口及包含块限制 |

此外可使用 inherit、initial、unset、revert 等 CSS 全局关键字。

## 相关知识点

- [CSS 定位与包含块](../../knowledge/frameworks-tools/k-fe0ffd0f-position.md)

## 追问题目

- [absolute 与 fixed 有什么区别？](q-60dc83c6-absolute-fixed.md)
- [fixed 与 sticky 有什么区别，sticky 为什么可能不生效？](q-a67dce12-fixed-sticky.md)
- [relative 相对于谁定位，left 是否生效？](q-62312ffd-relative-offset.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-10-frontend-and-os.md)
