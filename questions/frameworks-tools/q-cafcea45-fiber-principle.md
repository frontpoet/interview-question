---
id: "q-cafcea45"
title: "React Fiber 如何支持可中断渲染？"
category: "frameworks-tools"
tags: ["React"]
status: "ready"
type: "principle"
created: "2026-09-10"
updated: "2026-09-10"
scope: ["React Fiber 架构概念；内部字段不是稳定 API"]
relations:
  examines: ["k-7f44198d"]
  follow_up_to: ["q-af53944d"]
---

# React Fiber 如何支持可中断渲染？

## 题目

解释 Fiber 的工作单元、树结构、优先级和 Render/Commit 分工。

## 简要回答

Fiber 将协调工作表示成可逐步处理的节点，保存父子兄弟链接、状态、更新队列、优先级和变更标记。React 可在工作单元之间让出执行权，优先处理紧急更新，并恢复或重做未完成的 Render。

current 与 work-in-progress 分别表示当前树与准备中的结果；完成后由 Commit 应用变更。Render 的可中断不等于 Commit 也可任意中断。

Fiber 不是浏览器线程，不能抢占某个组件函数内部的长同步循环。并发能力需要相应调度路径，不能理解为每次渲染都会分片。内部字段是实现细节，随版本变化。

## 相关知识点

- [React Element 与 Fiber](../../knowledge/frameworks-tools/k-7f44198d-fiber.md)

## 原题目

- [虚拟 DOM 的原理是什么，为什么需要 key？](q-af53944d-virtual-dom.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-10-frontend-and-os.md)
