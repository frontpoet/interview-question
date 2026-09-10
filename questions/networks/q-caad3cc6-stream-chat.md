---
id: "q-caad3cc6"
title: "AI 对话的流式输出如何实现？"
category: "networks"
tags: ["HTTP","SSE","JavaScript"]
status: "ready"
type: "scenario"
created: "2026-09-10"
updated: "2026-09-10"
scope: ["单向文本流，以 SSE 为方案示例；不调用具体 AI 服务"]
relations:
  examines: ["k-61f823a5"]
---

# AI 对话的流式输出如何实现？

## 题目

说明后端格式、响应头、代理配置和前端渐进显示。

## 简要回答

后端边生成边写响应；浏览器增量接收，解析完整事件后追加文本。按字或按行显示也可由前端定时器模拟，因此视觉效果本身不能证明网络正在流式传输。

SSE 响应使用 `Content-Type: text/event-stream`，可用 `Cache-Control: no-cache`；禁用或调整应用、压缩和代理缓冲。请求可用 `Accept: text/event-stream` 协商，但这个头本身不会让服务端流式返回。

```text
event: delta
data: {"text":"你好"}

event: done
data: {}

```

每个事件后有空行；delta/done 是本例约定，不是 SSE 固定事件名。HTTP/1.1 可使用 chunked，HTTP/2 用自己的数据帧，无需手写 Transfer-Encoding。

## 分析与边界

前端用 EventSource 或 Fetch 流读取；保持跨块解码和分帧状态，不对每个网络块直接 JSON.parse。按帧合并界面更新，处理停止按钮、断连、错误事件和服务端取消。流式 Markdown 渲染应过滤不可信 HTML。

SSE 适合单向响应；若需要频繁双向通信，可评估 WebSocket。正常完成使用业务结束事件，连接断开不能一律当成功。

## 相关知识点

- [HTTP 流式响应与 SSE 分帧](../../knowledge/networks/k-61f823a5-stream.md)

## 追问题目

- [EventSource 不支持 POST 时如何接收 SSE？](q-bf0f9c2d-post-sse.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-10-frontend-and-os.md)
