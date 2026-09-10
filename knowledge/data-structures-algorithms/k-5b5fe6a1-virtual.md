---
id: "k-5b5fe6a1"
title: "虚拟列表与可见区计算"
category: "data-structures-algorithms"
tags: ["前端","性能"]
status: "ready"
created: "2026-09-10"
updated: "2026-09-10"
aliases: ["窗口化列表","Windowing"]
---

# 虚拟列表与可见区计算

## 核心概念

虚拟列表保留完整滚动范围，只渲染可见项和少量缓冲项，降低 DOM 数量。

## 原理与机制

定高列表用 scrollTop 除以行高定位首项，容器高度决定末项；占位层高为总条数乘行高，窗口内容平移到对应偏移。变高列表记录实测高度和前缀和，二分定位首项，尺寸变化后更新位置并保持滚动锚点。

## 适用边界与易错点

虚拟化不减少已加载数据本身的内存；网络分页是另一层优化。需要稳定 key，处理焦点、键盘、查找、无障碍、动态高度和滚动跳跃。

## 参考资料

- [TanStack Virtual：测量、overscan 和滚动定位](https://tanstack.com/virtual/latest/docs/api/virtualizer)

## 关联题目

- [虚拟列表如何实现，变高列表如何处理？](../../questions/data-structures-algorithms/q-e5d02f9a-virtual-list.md)
