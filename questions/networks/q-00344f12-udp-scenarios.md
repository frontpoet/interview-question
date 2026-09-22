---
id: "q-00344f12"
title: "UDP 适用于哪些场景，如何处理可靠性？"
category: "networks"
tags: ["TCP","UDP","网络"]
status: "ready"
type: "scenario"
created: "2026-09-22"
updated: "2026-09-22"
scope: ["按业务容忍丢包与延迟的程度选型"]
relations:
  examines: ["k-6561d6ac"]
---

# UDP 适用于哪些场景，如何处理可靠性？

## 题目

UDP 有哪些适用场景？为什么不能简单说它比 TCP 快？

## 简要回答

- 实时语音、视频：过期数据价值低，可用抖动缓冲、丢包隐藏或纠错换取较低延迟。
- 实时游戏：位置等状态可按序号丢弃旧包；关键操作另行确认重试。
- DNS 等小型查询：常用 UDP 降低交互开销，但存在 TCP 回退和其他传输方式。
- QUIC：使用 UDP 作为底层承载，在上层实现可靠性、加密和拥塞控制。

## 分析与边界

UDP 不建立 TCP 式连接，但没有自动重传、排序和可靠性保证。若应用补齐全部机制，复杂度与开销仍然存在；不能用 UDP 逃避拥塞控制，也不能把所有直播视频分发都说成 UDP（HLS/DASH 常基于 HTTP）。

## 相关知识点

- [TCP/IP 分层与 TCP、UDP 传输](../../knowledge/networks/k-6561d6ac-tcp-ip-udp.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-22-frontend-network-engineering.md)

