---
id: "q-7fe5632b"
title: "Chrome Performance 面板有什么用，录制哪些数据？"
category: "frameworks-tools"
tags: ["浏览器","性能"]
status: "ready"
type: "concept"
created: "2026-09-10"
updated: "2026-09-10"
scope: ["Chrome DevTools；轨道和选项随版本变化"]
relations:
  examines: ["k-c553f126","k-6e3c7224"]
  follow_up_to: ["q-284fd89e"]
---

# Chrome Performance 面板有什么用，录制哪些数据？

## 题目

说明如何从一段录制中定位卡顿或首屏瓶颈。

## 简要回答

面板按时间关联网络、主线程任务、脚本调用栈、样式计算、Layout、Paint、帧和交互，定位“时间花在哪里”。按设置还可记录截图、内存等信息；录制不是完整的数据包抓取，也不是每条 JS 指令的日志。

录制加载或明确交互后，先找长任务、LCP 或异常帧，再沿调用栈、Bottom-up/Call tree 和相关渲染事件定位代码。查看多次强制布局是否由读写交替造成。

保持相同测试环境，关闭干扰后对比优化前后。录制有开销；内存泄漏还需结合 Memory 面板和堆快照。

## 参考资料

- [Chrome：Performance 面板](https://developer.chrome.com/docs/devtools/performance/overview)

## 相关知识点

- [Web 性能指标与测量](../../knowledge/frameworks-tools/k-c553f126-vitals.md)
- [浏览器渲染流水线](../../knowledge/frameworks-tools/k-6e3c7224-render.md)

## 原题目

- [前端性能优化关注哪些指标？](q-284fd89e-performance-metrics.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-10-frontend-and-os.md)
