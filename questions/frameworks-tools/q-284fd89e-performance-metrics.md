---
id: "q-284fd89e"
title: "前端性能优化关注哪些指标？"
category: "frameworks-tools"
tags: ["浏览器","性能"]
status: "ready"
type: "concept"
created: "2026-09-10"
updated: "2026-09-10"
scope: ["2026-09-10 核对；实验室数据与真实用户数据分开解释"]
relations:
  examines: ["k-c553f126"]
---

# 前端性能优化关注哪些指标？

## 题目

区分用户体验指标与定位问题的辅助指标。

## 简要回答

| 目标 | 指标 |
| --- | --- |
| 主要内容出现 | LCP；FCP 辅助观察首次内容 |
| 交互响应 | INP；长任务和 TBT 辅助定位主线程阻塞 |
| 页面稳定 | CLS |
| 请求与资源 | TTFB、请求瀑布、缓存命中、传输体积 |
| 运行时流畅性 | 帧耗时、掉帧、内存增长、任务耗时 |

真实用户指标看分位数并按设备、网络、页面和版本分组。单次 Lighthouse 分数不能代表线上体验；首屏完成还需按业务定义，不能直接用 load 事件替代。

## 相关知识点

- [Web 性能指标与测量](../../knowledge/frameworks-tools/k-c553f126-vitals.md)

## 追问题目

- [如何检测 LCP，能否不改业务代码自动测量？](q-2da36d78-measure-lcp.md)
- [Chrome Performance 面板有什么用，录制哪些数据？](q-7fe5632b-performance-panel.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-10-frontend-and-os.md)
