---
id: "k-61f823a5"
title: "HTTP 流式响应与 SSE 分帧"
category: "networks"
tags: ["HTTP","SSE","JavaScript"]
status: "ready"
created: "2026-09-10"
updated: "2026-09-22"
aliases: ["Server-Sent Events","服务端推送事件"]
scope: ["浏览器 Fetch/EventSource；UTF-8 SSE"]
---

# HTTP 流式响应与 SSE 分帧

## 核心概念

HTTP 流式响应允许响应体尚未结束时读取数据。SSE 是在持续响应中按文本行编码事件的协议。

## 原理与机制

SSE 响应使用 `Content-Type: text/event-stream`。事件以空行结束，多个 data 行以换行合并；event 指定事件类型，id 支持续传标识，retry 表示重连间隔，冒号开头为注释。

字节块不等于字符、行或事件：先增量 UTF-8 解码，再跨块拼行，最后按空行分帧。服务端和代理均需及时转发，心跳可帮助维持空闲连接。

### 从流式输出到实时订阅

实时评论不止需要解析事件，还要约定消息 ID、游标、历史保留与断线补取。EventSource 的自动重连不会自动替业务端恢复数据库中的缺失消息；服务端必须根据 Last-Event-ID 或约定游标提供续传，客户端按业务 ID 去重。

## 适用边界与易错点

原生 EventSource 发 GET，自动解析和重连；Fetch 支持 POST 和自定义头，但解析、取消、重连、去重需应用负责。HTTP/2 不使用 HTTP/1.1 的 chunked 编码。SSE 单向下发，双向高频通信可考虑 WebSocket。

## 参考资料

- [WHATWG：SSE 格式和处理模型](https://html.spec.whatwg.org/multipage/server-sent-events.html)
- [MDN：使用 SSE](https://developer.mozilla.org/en-US/docs/Web/API/Server-sent_events/Using_server-sent_events)

## 关联题目

- [AI 对话的流式输出如何实现？](../../questions/networks/q-caad3cc6-stream-chat.md)
- [EventSource 不支持 POST 时如何接收 SSE？](../../questions/networks/q-bf0f9c2d-post-sse.md)
- [服务端主动推送涉及哪些前端技术？](../../questions/networks/q-ee9b8206-server-push-options.md)
