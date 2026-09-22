---
id: "q-ee9b8206"
title: "服务端主动推送涉及哪些前端技术？"
category: "networks"
tags: ["HTTP","SSE","WebSocket"]
status: "ready"
type: "comparison"
created: "2026-09-22"
updated: "2026-09-22"
scope: ["浏览器页面实时更新；后台系统通知单独讨论"]
relations:
  examines: ["k-8e81ec8d","k-61f823a5"]
---

# 服务端主动推送涉及哪些前端技术？

## 题目

服务端有新数据时，前端如何及时接收？如何选择 SSE、WebSocket 和轮询？

## 简要回答

页面在线且主要接收更新，可用 SSE；双向高频交互可用 WebSocket；环境限制下用长轮询或短轮询。HTTP 提交评论加 SSE 接收广播也是可行组合。网页未打开仍需通知时，评估 Push API、Service Worker 与通知授权。

## 分析与边界

选型看方向、频率、消息大小、代理支持及恢复需求。客户端负责连接状态、取消与卸载清理、退避重试、去重补拉和安全渲染。HTTP/2 Server Push 用于资源推送，不是评论消息订阅的替代接口。

## 相关知识点

- [实时消息传输与断线恢复](../../knowledge/networks/k-8e81ec8d-realtime-delivery.md)
- [HTTP 流式响应与 SSE 分帧](../../knowledge/networks/k-61f823a5-stream.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-22-frontend-network-engineering.md)

