---
id: "q-c25ddcb6"
title: "浏览器从资源到页面像素经历哪些步骤？"
category: "frameworks-tools"
tags: ["浏览器","性能"]
status: "ready"
type: "principle"
created: "2026-09-10"
updated: "2026-09-10"
relations:
  examines: ["k-6e3c7224"]
---

# 浏览器从资源到页面像素经历哪些步骤？

## 题目

说明 DOM、样式、布局、绘制和合成，以及脚本的影响。

## 简要回答

浏览器解析 HTML 构建 DOM，加载 CSS 并计算样式，然后布局确定几何位置，生成绘制记录、栅格化，再合成显示。过程可渐进执行，不等待所有图片下载完。

普通同步脚本可能阻塞解析；defer 通常在解析完成后按顺序执行，async 就绪后执行且顺序不固定。CSS 会影响渲染，并可能间接影响等待样式的脚本。

几何属性变化可能触发布局，外观变化可能触发绘制，合适的变换可能主要走合成。连续交替写样式和读布局会造成强制同步布局。

## 相关知识点

- [浏览器渲染流水线](../../knowledge/frameworks-tools/k-6e3c7224-render.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-10-frontend-and-os.md)
