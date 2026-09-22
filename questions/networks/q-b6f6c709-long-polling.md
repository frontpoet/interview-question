---
id: "q-b6f6c709"
title: "长轮询如何工作，有哪些代价？"
category: "networks"
tags: ["HTTP"]
status: "ready"
type: "principle"
created: "2026-09-22"
updated: "2026-09-22"
scope: ["支持游标补取的 HTTP 增量接口"]
relations:
  examines: ["k-8e81ec8d"]
---

# 长轮询如何工作，有哪些代价？

## 题目

解释长轮询，与短轮询、持续流式响应有何不同？

## 简要回答

客户端携带游标发请求；服务端有增量就返回，没有则挂起到约定超时，再返回空结果；客户端处理成功后更新游标，继续下一轮。短轮询按固定间隔请求；SSE 则在同一个响应里持续传事件。

## 分析与边界

每个订阅维持一个在途请求，避免重叠引起乱序。约定服务端等待时长小于网关超时，并区分正常空响应和故障；故障采用带随机抖动的退避，离页时用 AbortController 取消。响应结束到下一次请求之间的事件必须能按游标补取，不能只用内存里的“当前连接”保存消息。大量挂起请求仍消耗连接和服务端资源，宜采用异步 I/O。

## 相关知识点

- [实时消息传输与断线恢复](../../knowledge/networks/k-8e81ec8d-realtime-delivery.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-22-frontend-network-engineering.md)

