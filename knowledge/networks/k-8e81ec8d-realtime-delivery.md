---
id: "k-8e81ec8d"
title: "实时消息传输与断线恢复"
category: "networks"
tags: ["HTTP","SSE","WebSocket"]
status: "ready"
created: "2026-09-22"
updated: "2026-09-22"
---

# 实时消息传输与断线恢复

## 核心概念

实时更新需要消息通道，也需要消息标识、恢复位置和客户端消费策略。传输连接成功不代表业务消息恰好处理一次。

## 原理与机制

| 方式 | 交互模型 | 主要成本 |
| --- | --- | --- |
| 短轮询 | 定期发请求取增量 | 空请求与轮询延迟 |
| 长轮询 | 服务端等到有消息或超时才响应，客户端再发下一次 | 重连请求与大量挂起连接 |
| SSE | HTTP 响应持续发送文本事件 | 单向下发；原生 EventSource 主要用于 GET |
| WebSocket | 建立持续双向消息通道 | 应用负责重连、心跳、鉴权续期和恢复 |

WebSocket 浏览器接口由 [WHATWG WebSockets](https://websockets.spec.whatwg.org/) 定义；SSE 的事件 ID 和重连规则见 [HTML SSE](https://html.spec.whatwg.org/multipage/server-sent-events.html)。

业务消息附 roomId、messageId、单房间递增序号或可恢复游标。重连时从最后成功应用的位置补拉；重发时按 ID 去重。历史超出保留窗口则重新取得快照，再衔接增量。

## 适用边界与易错点

心跳确认连接活性，不能代替业务确认。标准 WebSocket API 没有自动接收背压；持续积压需限流、批处理或切换快照。页面关闭后的系统通知可用 Push API 配合 Service Worker，与打开页面里的实时评论通道是不同需求。

## 关联题目

- [服务端主动推送涉及哪些前端技术？](../../questions/networks/q-ee9b8206-server-push-options.md)
- [长轮询如何工作，有哪些代价？](../../questions/networks/q-b6f6c709-long-polling.md)
- [直播比赛中如何实时加载评论？](../../questions/system-design/q-ff51ab3c-live-comments.md)

