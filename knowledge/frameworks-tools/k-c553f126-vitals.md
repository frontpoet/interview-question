---
id: "k-c553f126"
title: "Web 性能指标与测量"
category: "frameworks-tools"
tags: ["浏览器","性能"]
status: "ready"
created: "2026-09-10"
updated: "2026-09-10"
aliases: ["Web 性能测量"]
scope: ["2026-09-10 核对；实验室数据与真实用户数据分开解释"]
---

# Web 性能指标与测量

## 核心概念

性能测量区分加载、交互和视觉稳定性，也区分固定环境的实验室数据与真实访问数据。

## 原理与机制

Core Web Vitals 包括 LCP、INP、CLS。良好阈值分别为不超过 2.5 秒、200 毫秒、0.1；真实用户评估按移动端和桌面端分别看第 75 百分位。FCP、TTFB、长任务和传输体积用于进一步定位。

LCP 随候选元素变化更新，不能把第一个候选当最终结果。线上可用 web-vitals 处理页面生命周期；Lighthouse CI 可固定环境回归，DevTools trace 可定位主线程瓶颈。

## 适用边界与易错点

LCP 不等于所有资源加载结束，INP 不等于首次交互或 TBT。单次实验室分数不能代表用户分布；自动化测量须固定设备、网络、缓存和测试路径。

## 参考资料

- [web.dev：Web Vitals](https://web.dev/articles/vitals)
- [web.dev：LCP](https://web.dev/articles/lcp)

## 关联题目

- [如何实现接近真实页面的骨架屏？](../../questions/frameworks-tools/q-17617362-skeleton.md)
- [前端性能优化关注哪些指标？](../../questions/frameworks-tools/q-284fd89e-performance-metrics.md)
- [如何检测 LCP，能否不改业务代码自动测量？](../../questions/frameworks-tools/q-2da36d78-measure-lcp.md)
- [Chrome Performance 面板有什么用，录制哪些数据？](../../questions/frameworks-tools/q-7fe5632b-performance-panel.md)
- [如何系统优化首屏、请求、渲染和打包性能？](../../questions/frameworks-tools/q-c374ef0f-frontend-optimization.md)
