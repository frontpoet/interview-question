---
id: "q-e5d02f9a"
title: "虚拟列表如何实现，变高列表如何处理？"
category: "data-structures-algorithms"
tags: ["前端","性能"]
status: "ready"
type: "principle"
created: "2026-09-10"
updated: "2026-09-10"
relations:
  examines: ["k-5b5fe6a1"]
---

# 虚拟列表如何实现，变高列表如何处理？

## 题目

给出定高列表的可见区算法，并说明变高扩展。

## 简要回答

保留总高度占位，只渲染视口附近的项；滚动时更新窗口范围，用 translateY 或绝对定位将窗口放到正确位置。overscan 减少快速滚动白屏，不能设得接近全量。

## 定高计算示例

约定 count 为非负整数、rowHeight 为正数、viewportHeight 非负、overscan 为非负整数；scrollTop 可以因浏览器回弹越界，计算时钳制。返回半开区间 `[start, end)`。

```js
function getRange(count, rowHeight, viewportHeight, scrollTop, overscan = 3) {
  const totalHeight = count * rowHeight;
  const y = Math.max(0, Math.min(scrollTop, Math.max(0, totalHeight - viewportHeight)));
  const start = Math.max(0, Math.floor(y / rowHeight) - overscan);
  const end = Math.min(count, Math.ceil((y + viewportHeight) / rowHeight) + overscan);
  return { start, end, offset: start * rowHeight, totalHeight };
}
```

范围计算 O(1)，DOM 数量 O(可见项 + 缓冲项)。容器设 overflow，内部占位高 totalHeight，渲染 `items.slice(start, end)` 并偏移 offset。滚动更新可用 requestAnimationFrame 合并。

## 分析与边界

变高列表用预估高度初始化，ResizeObserver 测量后更新前缀和，二分定位滚动位置；普通前缀数组更新可为 O(n)，大规模动态更新可用树状数组等结构。修正视口前方高度时维持锚点，避免跳动。保留稳定 key、焦点和无障碍语义；虚拟化不代替分页加载。

## 相关知识点

- [虚拟列表与可见区计算](../../knowledge/data-structures-algorithms/k-5b5fe6a1-virtual.md)

## 示例验证

在 Node 中验证空列表、视口大于内容、回弹偏移、末尾越界和非整行偏移；未进行浏览器滚动与动态高度集成测试。

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-10-frontend-and-os.md)
