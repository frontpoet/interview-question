---
id: "k-df1ca75c"
title: "进程与线程的资源和执行模型"
category: "operating-systems"
tags: ["操作系统"]
status: "ready"
created: "2026-09-10"
updated: "2026-09-10"
aliases: ["进程与线程"]
scope: ["以现代 Linux/POSIX 线程模型为例"]
---

# 进程与线程的资源和执行模型

## 核心概念

进程提供地址空间与资源隔离边界，线程是进程内的执行流。具体调度对象取决于操作系统实现。

## 原理与机制

同进程线程共享地址空间、堆和文件描述符等资源，各自保存寄存器、栈、线程标识等执行状态。进程间地址空间通常隔离，可用显式共享内存等方式交换数据。

## 适用边界与易错点

线程切换可能避免地址空间切换，但并不保证总比进程切换快；缓存、调度和同步开销影响结果。线程故障可能破坏整个进程，进程隔离也不是绝对安全保证。

## 参考资料

- [Linux man-pages：pthreads](https://man7.org/linux/man-pages/man7/pthreads.7.html)

## 关联题目

- [进程之间有哪些通信方式，如何选择？](../../questions/operating-systems/q-aa7d6f0c-ipc-methods.md)
- [进程和线程有什么区别？](../../questions/operating-systems/q-182ad9c8-process-thread.md)
