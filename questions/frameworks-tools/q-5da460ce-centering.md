---
id: "q-5da460ce"
title: "如何用 CSS 实现元素水平和垂直居中？"
category: "frameworks-tools"
tags: ["CSS"]
status: "draft"
type: "concept"
created: "2026-09-10"
updated: "2026-09-10"
scope: ["暂将原文“属性居中”理解为“元素居中”；默认横向书写"]
relations:
  examines: ["k-7e045f7e","k-fe0ffd0f"]
---

# 如何用 CSS 实现元素水平和垂直居中？

## 题目

按文本、普通块元素和浮层分别说明居中方法。

## 简要回答

- 行内内容水平居中：父元素 `text-align: center`。
- 普通块盒水平居中：限制宽度后使用 `margin-inline: auto`。
- 双轴居中：父元素 Flex 配合 `justify-content: center; align-items: center`，或 Grid 配合 `place-items: center`。
- 浮层居中：absolute 配合 `top: 50%; left: 50%; transform: translate(-50%, -50%)`，父容器需建立合适包含块。

垂直居中须有可分配高度，百分比高度还依赖包含块。`line-height` 只适用于有限的单行文本场景。

## 示例

```css
.container {
  display: grid;
  min-height: 20rem;
  place-items: center;
}
```

## 待确认

原文为“属性居中的方法”，未说明居中对象；当前按元素居中整理。

## 相关知识点

- [CSS 盒模型与布局](../../knowledge/frameworks-tools/k-7e045f7e-css-layout.md)
- [CSS 定位与包含块](../../knowledge/frameworks-tools/k-fe0ffd0f-position.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-10-frontend-and-os.md)
