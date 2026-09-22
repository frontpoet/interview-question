---
id: "k-6561d6ac"
title: "TCP/IP 分层与 TCP、UDP 传输"
category: "networks"
tags: ["TCP","UDP","网络"]
status: "ready"
created: "2026-09-22"
updated: "2026-09-22"
---

# TCP/IP 分层与 TCP、UDP 传输

## 核心概念

TCP/IP 通常指互联网协议族，而非一个协议。常见四层模型为链路层、网际层、传输层、应用层，各层负责不同问题。

## 原理与机制

链路层在本地链路传递帧；IP 负责寻址和跨网络转发，但不保证到达或顺序。TCP 在 IP 上提供可靠、有序的字节流，用序号、确认、重传、流量控制和拥塞控制管理传输；没有业务消息边界，也不内置加密。UDP 提供带端口的数据报，保留消息边界，不内置可靠交付、排序或拥塞控制。参见 [TCP 标准 RFC 9293](https://www.rfc-editor.org/rfc/rfc9293.html)。

## 适用边界与易错点

UDP 适合应用自行权衡延迟和可靠性：实时音视频可容忍少量丢包，游戏状态可用新状态替代旧状态，DNS 常用 UDP 但也会使用 TCP。QUIC 在 UDP 上实现可靠流、拥塞控制与安全，HTTP/3 因而不基于 TCP。UDP 并非必然更快，应用仍需控制速率与报文大小，避免拥塞和 IP 分片；参见 [RFC 8085](https://www.rfc-editor.org/rfc/rfc8085.html)。

## 关联题目

- [TCP/IP 协议族用来解决什么问题？](../../questions/networks/q-3c04d3b9-tcp-ip-purpose.md)
- [UDP 适用于哪些场景，如何处理可靠性？](../../questions/networks/q-00344f12-udp-scenarios.md)

