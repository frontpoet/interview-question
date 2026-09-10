---
id: "q-ce38d22b"
title: "display 如何影响元素的外部布局和内部布局？"
category: "frameworks-tools"
tags: ["CSS"]
status: "ready"
type: "concept"
created: "2026-09-10"
updated: "2026-09-10"
scope: ["浏览器 CSS；默认横向书写模式"]
relations:
  examines: ["k-7e045f7e"]
---

# display 如何影响元素的外部布局和内部布局？

## 题目

介绍 block、inline、inline-block、flex、grid、none 和 contents。

## 简要回答

- block 通常生成块级盒；inline 参与行内排版。
- inline-block 外部按行内原子盒排版，内部建立独立格式化上下文，可设置宽高。
- flex/grid 建立对应内部布局；inline-flex/inline-grid 的外部参与方式为行内。
- none 不生成布局盒；contents 通常去掉元素自身盒，让子元素参与布局，特殊元素和无障碍行为需检查。

不要把 display 只理解为“显示或隐藏”。隐藏但保留空间可考虑 visibility。

## 相关知识点

- [CSS 盒模型与布局](../../knowledge/frameworks-tools/k-7e045f7e-css-layout.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-10-frontend-and-os.md)
