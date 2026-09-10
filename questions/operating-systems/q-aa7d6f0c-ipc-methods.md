---
id: "q-aa7d6f0c"
title: "进程之间有哪些通信方式，如何选择？"
category: "operating-systems"
tags: ["操作系统"]
status: "ready"
type: "comparison"
created: "2026-09-10"
updated: "2026-09-10"
scope: ["以 Linux/POSIX 为例，Windows API 不同","以现代 Linux/POSIX 线程模型为例"]
relations:
  examines: ["k-8775ea6f","k-df1ca75c"]
---

# 进程之间有哪些通信方式，如何选择？

## 题目

比较常用 IPC 的数据形式与使用场景。

## 简要回答

| 方式 | 特点与场景 |
| --- | --- |
| 匿名管道 / FIFO | 字节流，常用于命令流水线或本机进程通信 |
| 消息队列 | 有消息边界，适合离散消息传递 |
| 共享内存 | 大量数据交换，需额外同步和生命周期管理 |
| Unix 域套接字 | 本机双向通信，可有流或数据报形式 |
| 网络套接字 | 可跨主机，需要处理协议、失败和安全 |
| 信号 / 信号量 | 前者用于通知，后者主要用于同步 |

按是否跨机、数据量、边界要求、复制成本和同步复杂度选择。共享内存不自动解决竞态，流式管道不自动保留应用消息边界。

## 相关知识点

- [进程间通信与同步](../../knowledge/operating-systems/k-8775ea6f-ipc.md)
- [进程与线程的资源和执行模型](../../knowledge/operating-systems/k-df1ca75c-process.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-10-frontend-and-os.md)
