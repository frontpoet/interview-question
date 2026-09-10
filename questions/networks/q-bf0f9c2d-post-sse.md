---
id: "q-bf0f9c2d"
title: "EventSource 不支持 POST 时如何接收 SSE？"
category: "networks"
tags: ["HTTP","SSE","JavaScript"]
status: "ready"
type: "principle"
created: "2026-09-10"
updated: "2026-09-10"
scope: ["现代浏览器 Fetch 和 Streams；本例只解析 event/data，不实现自动重连"]
relations:
  examines: ["k-61f823a5"]
  follow_up_to: ["q-caad3cc6"]
---

# EventSource 不支持 POST 时如何接收 SSE？

## 题目

发送 JSON POST 请求并持续读取 SSE，处理分块、UTF-8 和事件边界。

## 简要回答

使用 Fetch 的 POST 和 response.body，先验证状态与 Content-Type，再增量解码并解析 SSE。原生 EventSource 的重连、id 续传和重试行为不会自动继承。

## 接收示例

本例与服务端约定 event/data、UTF-8、空行结束事件；忽略其他字段。完整 EventSource 兼容实现还需处理 id、retry 和重连。本例设置单事件大小上限，生产值按业务调整。

```js
async function* parseSSE(body) {
  const reader = body.pipeThrough(new TextDecoderStream()).getReader();
  let line = '', data = [], event = '', skipLF = false, size = 0;
  function consumeLine() {
    if (line === '') {
      const result = data.length ? { event: event || 'message', data: data.join('\n') } : null;
      data = []; event = ''; size = 0;
      return result;
    }
    if (!line.startsWith(':')) {
      const colon = line.indexOf(':');
      const field = colon < 0 ? line : line.slice(0, colon);
      let value = colon < 0 ? '' : line.slice(colon + 1);
      if (value.startsWith(' ')) value = value.slice(1);
      if (field === 'data') data.push(value);
      if (field === 'event') event = value;
    }
    return null;
  }
  try {
    while (true) {
      const { value, done } = await reader.read();
      if (done) break;
      for (const ch of value) {
        if (skipLF) { skipLF = false; if (ch === '\n') continue; }
        if (++size > 1024 * 1024) throw new Error('SSE event too large');
        if (ch === '\r' || ch === '\n') {
          const frame = consumeLine();
          line = ''; skipLF = ch === '\r';
          if (frame) yield frame;
        } else line += ch;
      }
    }
    // 未以空行结束的事件不派发。
  } finally {
    try { await reader.cancel(); } finally { reader.releaseLock(); }
  }
}

async function streamChat(prompt, onText, signal) {
  const response = await fetch('/api/chat', {
    method: 'POST', signal,
    headers: { 'Content-Type': 'application/json', Accept: 'text/event-stream' },
    body: JSON.stringify({ prompt })
  });
  if (!response.ok) throw new Error(`HTTP ${response.status}`);
  const mime = (response.headers.get('content-type') || '').split(';')[0].trim().toLowerCase();
  if (mime !== 'text/event-stream' || !response.body) throw new Error('Expected SSE');
  for await (const frame of parseSSE(response.body)) {
    if (frame.event === 'done') return;
    if (frame.event === 'error') throw new Error(frame.data);
    if (frame.event === 'delta') {
      const payload = JSON.parse(frame.data);
      if (typeof payload.text !== 'string') throw new Error('Invalid delta');
      onText(payload.text);
    }
  }
  throw new Error('Stream ended before done');
}
```

调用方捕获错误，使用 AbortController 取消，并把文本作为文本渲染。总解析时间 O(n)，缓冲受单事件上限约束。跨域 JSON POST 或 Authorization 常触发预检，服务端须允许对应方法和头。

另一方案是 POST 创建任务，再用 EventSource GET 订阅任务 ID；应绑定用户权限，避免任务 ID 成为可越权读取的凭证。POST 自动重试还需幂等键，避免重复生成。

## 参考资料

- [MDN：Fetch 的流式响应体](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch)

## 相关知识点

- [HTTP 流式响应与 SSE 分帧](../../knowledge/networks/k-61f823a5-stream.md)

## 原题目

- [AI 对话的流式输出如何实现？](q-caad3cc6-stream-chat.md)

## 示例验证

在 Node Web Streams 中验证 UTF-8 多字节字符、BOM、所有单切分位置、逐字节输入、CR/LF/CRLF、多行 data、未完成帧、大小限制、取消及错误响应。Fetch 使用本地模拟响应，未连接真实后端或代理。

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-10-frontend-and-os.md)
