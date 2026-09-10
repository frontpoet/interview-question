---
id: "k-8775ea6f"
title: "进程间通信与同步"
category: "operating-systems"
tags: ["操作系统"]
status: "ready"
created: "2026-09-10"
updated: "2026-09-10"
aliases: ["IPC","Inter-Process Communication"]
scope: ["以 Linux/POSIX 为例，Windows API 不同"]
relations:
  prerequisite: ["k-df1ca75c"]
---

# 进程间通信与同步

## 核心概念

IPC 在进程之间交换数据或协调执行。传输机制和同步机制可组合使用。

## 原理与机制

管道和 FIFO 传递字节流；消息队列保留消息边界；共享内存把数据映射给多个进程；Unix 域套接字用于本机通信，网络套接字可跨主机。信号适合事件通知，信号量主要协调资源访问。

## 适用边界与易错点

共享内存减少传输复制，但需同步和内存可见性设计；字节流需应用分帧。比较方案时考虑边界、吞吐、复制、同步和部署范围，不只比较速度。

## 参考资料

- [Linux man-pages：System V IPC](https://man7.org/linux/man-pages/man7/svipc.7.html)
- [Linux man-pages：pipe](https://man7.org/linux/man-pages/man7/pipe.7.html)
- [Linux man-pages：Unix sockets](https://man7.org/linux/man-pages/man7/unix.7.html)

## 前置知识

- [进程与线程的资源和执行模型](k-df1ca75c-process.md)

## 关联题目

- [进程之间有哪些通信方式，如何选择？](../../questions/operating-systems/q-aa7d6f0c-ipc-methods.md)
