---
id: "q-17617362"
title: "如何实现接近真实页面的骨架屏？"
category: "frameworks-tools"
tags: ["CSS","性能","浏览器"]
status: "ready"
type: "scenario"
created: "2026-09-10"
updated: "2026-09-10"
scope: ["页面包含图片、文字和异步组件；目标是渐进展示并减少布局偏移"]
relations:
  examines: ["k-83719588","k-c553f126"]
---

# 如何实现接近真实页面的骨架屏？

## 题目

页面有多种组件时，如何在资源加载完成前展示合理占位？

## 简要回答

- 按卡片、列表、头像、表格等设计骨架，复用真实组件的 Layout、间距和响应式规则。
- 图片约定 width/height 或 aspect-ratio；文本占位使用接近最终行数和行高。
- 各区域独立就绪，先显示已知文字，图片区域继续占位，加载或解码就绪后替换。
- 首屏占位写入初始 HTML/SSR 并提供关键 CSS，不能等全部应用 JS 加载后才出现。
- 显式处理加载、空态、失败和重试；动画遵守 reduced-motion，装饰占位不反复播报给屏幕阅读器。

## 分析与边界

不依赖 window.load 作为整页替换门槛；它不是业务数据就绪信号。未知内容无法精确预测，优先保留稳定区域并测量 CLS。骨架改善等待感，不代表 LCP 或实际请求时间自动改善。

## 相关知识点

- [渐进加载与布局稳定性](../../knowledge/frameworks-tools/k-83719588-loading.md)
- [Web 性能指标与测量](../../knowledge/frameworks-tools/k-c553f126-vitals.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-10-frontend-and-os.md)
