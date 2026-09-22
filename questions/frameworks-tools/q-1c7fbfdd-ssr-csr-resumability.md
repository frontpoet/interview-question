---
id: "q-1c7fbfdd"
title: "SSR、CSR 与 Resumable SSR 有何区别，首屏与交互谁更快？"
category: "frameworks-tools"
tags: ["前端","SSR","性能"]
status: "ready"
type: "comparison"
created: "2026-09-22"
updated: "2026-09-22"
scope: ["对比首次加载；不存在脱离应用和设备的固定性能排序"]
relations:
  examines: ["k-f7b2349f"]
---

# SSR、CSR 与 Resumable SSR 有何区别，首屏与交互谁更快？

## 题目

比较 SSR 和 CSR 的优缺点，解释 resumable SSR，讨论首屏、可交互时间及 SSR 难点。

## 简要回答

| 维度 | CSR | 传统交互式 SSR | Resumable SSR |
| --- | --- | --- | --- |
| 初始内容 | 常需下载并执行 JS 后生成 | 服务端 HTML 可先显示 | 服务端 HTML 携带恢复信息 |
| 客户端交互 | 应用运行并渲染后可交互 | 自定义交互通常需水合 | 按事件入口按需恢复 |
| 主要成本 | 客户端计算、JS/数据瀑布 | 服务端渲染 + 客户端水合 | 序列化、框架约束与代码按需加载 |
| 适用倾向 | 富交互后台、后续导航 | 需要较早内容、SEO 等页面 | 希望减少初始客户端执行的合适项目 |

SSR 常能更早显示内容，但慢后端、冷启动或缓存差会拖慢首屏；CSR 命中缓存也可能很快。可交互速度取决于 JS 体积、水合量、设备、预加载和具体控件，不能无条件给出谁更快。Qwik 类方案减少整体水合成本，首次点击仍可能等待处理代码下载。

## 分析与边界

SSR 难点包括 window/document 不存在、输出不一致引起 hydration mismatch、请求间状态污染、序列化敏感数据、个性化缓存隔离、流式错误处理和部署开销。应分别测 TTFB、FCP/LCP 与具体交互延迟；INP 是交互响应指标，不能直接当成“水合完成时刻”。SSR 原生链接可能立即可用，而未水合的自定义控件尚不可用。

## 相关知识点

- [CSR、SSR、水合与可恢复执行](../../knowledge/frameworks-tools/k-f7b2349f-rendering-hydration-resume.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-22-frontend-network-engineering.md)

