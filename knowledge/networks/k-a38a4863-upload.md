---
id: "k-a38a4863"
title: "分片上传与断点续传"
category: "networks"
tags: ["HTTP","前端"]
status: "ready"
created: "2026-09-10"
updated: "2026-09-22"
aliases: ["断点续传","分片上传"]
---

# 分片上传与断点续传

## 核心概念

分片上传拆分大文件，断点续传依靠服务端确认的进度恢复传输。切片本身不提供可靠性。

## 原理与机制

会话标识绑定用户和文件；客户端以受控并发提交片段，服务端保存片号或偏移，检查幂等、长度和校验和。完成时确认全部片段并原子发布结果。tus 核心采用偏移协议；并行拼接属于额外能力，不能把任意分片 API 都称为 tus。

### 上传数量限制

文件级配额应按 uploadId 原子预留，完成后确认，取消或过期后释放；重试不得重复占额。限制同时上传文件数与限制分片请求并发是两个维度，客户端队列不能替代服务端约束。对象存储直传同样需要在授权、预留和完成确认处校验额度。

## 适用边界与易错点

文件名不能作为唯一标识，已发送字节不等于已持久化字节。恢复前查询服务端状态；设置过期清理、大小限制、鉴权及内容检查。

## 参考资料

- [tus：恢复上传协议](https://tus.io/protocols/resumable-upload)
- [MDN：Blob.slice](https://developer.mozilla.org/en-US/docs/Web/API/Blob/slice)

## 关联题目

- [如何设计大文件分片上传与断点续传？](../../questions/system-design/q-602a0ded-chunk-upload.md)
- [服务器如何限制上传文件数量、并发与频率？](../../questions/system-design/q-a86f1bde-upload-limits.md)
