---
id: "k-6e3c7224"
title: "浏览器渲染流水线"
category: "frameworks-tools"
tags: ["浏览器","性能"]
status: "ready"
created: "2026-09-10"
updated: "2026-09-10"
aliases: []
---

# 浏览器渲染流水线

## 核心概念

浏览器把 HTML、CSS 和脚本产生的状态转换成像素，主要涉及解析、样式计算、布局、绘制和合成。

## 原理与机制

HTML 解析形成 DOM，CSS 参与样式计算；布局计算盒的几何信息，绘制产生绘制记录，栅格化生成像素，合成组合图层。资源加载与这些步骤可交错进行。

几何变化可能触发布局；颜色变化通常只需绘制；某些 transform/opacity 更新可主要在合成阶段处理。布局写入后立即读取尺寸可能迫使浏览器提前执行布局。

## 适用边界与易错点

重排并非总对全页面执行，重绘也不一定先有重排。DOM 更新不等于像素已经显示，React Commit 与浏览器绘制是不同步骤。

## 参考资料

- [MDN：浏览器如何工作](https://developer.mozilla.org/en-US/docs/Web/Performance/Guides/How_browsers_work)

## 关联题目

- [Chrome Performance 面板有什么用，录制哪些数据？](../../questions/frameworks-tools/q-7fe5632b-performance-panel.md)
- [浏览器从资源到页面像素经历哪些步骤？](../../questions/frameworks-tools/q-c25ddcb6-browser-rendering.md)
- [如何系统优化首屏、请求、渲染和打包性能？](../../questions/frameworks-tools/q-c374ef0f-frontend-optimization.md)
- [React 组件从 setState 到显示更新经历哪些步骤？](../../questions/frameworks-tools/q-d2f67a35-react-update.md)
