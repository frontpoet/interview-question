---
id: "q-2da36d78"
title: "如何检测 LCP，能否不改业务代码自动测量？"
category: "frameworks-tools"
tags: ["浏览器","性能"]
status: "ready"
type: "principle"
created: "2026-09-10"
updated: "2026-09-10"
scope: ["支持 Largest Contentful Paint API 的浏览器；自动化结果为实验室数据"]
relations:
  examines: ["k-c553f126"]
  follow_up_to: ["q-284fd89e"]
---

# 如何检测 LCP，能否不改业务代码自动测量？

## 题目

说明线上采集、手动定位和自动回归三种方式。

## 简要回答

线上可用 web-vitals 的 onLCP，处理候选更新和页面生命周期；手动用 Chrome Performance 记录并定位 LCP 元素。实验室可用 Lighthouse CLI/CI，不修改业务代码；也可由浏览器自动化在导航前注入观察器。

```js
let lastCandidate;
if (PerformanceObserver.supportedEntryTypes.includes('largest-contentful-paint')) {
  const observer = new PerformanceObserver(list => {
    for (const entry of list.getEntries()) lastCandidate = entry;
  });
  observer.observe({ type: 'largest-contentful-paint', buffered: true });
}
```

这只是候选观察示意，不能直接当完整线上 LCP 实现；还需处理隐藏、交互、页面恢复等生命周期及最终上报。

## 自动化方案

在 CI 启动生产构建，固定测试 URL、视口、CPU/网络限速和缓存条件，运行 Lighthouse 多次，按约定统计值检查 LCP 预算并保存报告。登录页需提供合成账号和固定数据，不采真实用户凭证。

无业务埋点也可查看有足够公开数据的 CrUX/PageSpeed Insights 真实用户统计，但不能保证每个 URL 都有数据。自动化导航测试不能代表完整真实用户 INP。

## 参考资料

- [Lighthouse CI：自动运行和回归检查](https://github.com/GoogleChrome/lighthouse-ci)
- [web.dev：LCP API 及测量差异](https://web.dev/articles/lcp)

## 相关知识点

- [Web 性能指标与测量](../../knowledge/frameworks-tools/k-c553f126-vitals.md)

## 原题目

- [前端性能优化关注哪些指标？](q-284fd89e-performance-metrics.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-10-frontend-and-os.md)
