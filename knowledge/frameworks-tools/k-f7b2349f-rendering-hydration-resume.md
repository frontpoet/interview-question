---
id: "k-f7b2349f"
title: "CSR、SSR、水合与可恢复执行"
category: "frameworks-tools"
tags: ["前端","SSR","性能"]
status: "ready"
created: "2026-09-22"
updated: "2026-09-22"
scope: ["通用渲染概念；传统水合以 React 为例，resumability 以 Qwik 为例"]
---

# CSR、SSR、水合与可恢复执行

## 核心概念

CSR 由客户端执行应用代码生成主要内容；SSR 在服务器生成 HTML。传统交互式 SSR 通常需要 hydration（水合）在客户端恢复框架状态和事件处理。服务端渲染的原生链接、表单等能力不必等待框架水合。

## 原理与机制

CSR 常经历 HTML → JS → 数据 → 渲染，数据预取和缓存可缩短路径；SSR 可把已有内容先交给浏览器，但会增加服务端计算，且水合需要客户端代码和计算。流式 SSR 可逐段输出，减少等待整个页面完成的时间。

Resumability（可恢复执行）把客户端后续运行所需的状态和事件入口等信息随服务端 HTML 序列化，使浏览器按需继续执行，避免为恢复状态而重跑整个组件树。Qwik 是代表实现，参见 [Qwik：Resumable](https://qwik.dev/docs/concepts/resumable/)。它仍有引导脚本、序列化大小、预取及首次交互按需加载的成本，并非“无需 JS”。

## 适用边界与易错点

SSR 不保证 TTFB、LCP 或首次交互一定优于 CSR。水合时服务端与客户端初始输出需要一致；时间、随机数、时区、浏览器专属 API、无效 HTML 都可能导致不匹配，参见 [React hydrateRoot](https://react.dev/reference/react-dom/client/hydrateRoot)。还需处理每请求状态隔离、用户级缓存、序列化安全和后端负载；共享全局用户状态可能泄露数据。

## 关联题目

- [SSR、CSR 与 Resumable SSR 有何区别，首屏与交互谁更快？](../../questions/frameworks-tools/q-1c7fbfdd-ssr-csr-resumability.md)

