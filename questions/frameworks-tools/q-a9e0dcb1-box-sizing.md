---
id: "q-a9e0dcb1"
title: "什么是 CSS 盒模型，box-sizing 如何影响尺寸？"
category: "frameworks-tools"
tags: ["CSS"]
status: "ready"
type: "concept"
created: "2026-09-22"
updated: "2026-09-22"
scope: ["普通块盒；无额外布局约束"]
relations:
  examines: ["k-7e045f7e"]
---

# 什么是 CSS 盒模型，box-sizing 如何影响尺寸？

## 题目

解释盒模型和 box-sizing，并计算 width: 200px、padding: 10px、border: 2px solid 时的边框盒宽度。

## 简要回答

盒模型从内向外包括 content、padding、border、margin。content-box 的 width 指内容宽度，边框盒宽度为 200 + 20 + 4 = 224px；border-box 的 width 包含内边距和边框，边框盒为 200px，内容宽度为 176px。两者都不包含 margin。

## 分析与边界

可统一设置 `*, *::before, *::after { box-sizing: border-box; }` 便于尺寸计算；该属性默认不继承。实际尺寸还受 min/max、Flex/Grid 布局、内容和元素类型影响。示例假设普通块盒、尺寸约束不冲突；content-box 下给 width: 100% 再加 padding 可能溢出。

## 相关知识点

- [CSS 盒模型与布局](../../knowledge/frameworks-tools/k-7e045f7e-css-layout.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-22-frontend-network-engineering.md)

