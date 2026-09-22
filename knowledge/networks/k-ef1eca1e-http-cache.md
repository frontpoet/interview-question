---
id: "k-ef1eca1e"
title: "HTTP 缓存与静态资源版本"
category: "networks"
tags: ["HTTP","构建","性能"]
status: "ready"
created: "2026-09-10"
updated: "2026-09-22"
aliases: []
---

# HTTP 缓存与静态资源版本

## 核心概念

缓存按新鲜度复用响应，过期后可用验证器确认资源是否变化。内容哈希用于区分不可变资源版本。

## 原理与机制

Cache-Control 指定缓存策略，ETag/If-None-Match 等支持验证。带内容哈希的静态资源可长缓存，HTML 和版本清单需及时验证或短缓存，使入口能指向新版本。

### 新鲜度与条件验证

通常先判断响应能否存储、请求是否匹配缓存键和 Vary，再判断是否新鲜。响应 max-age 指定新鲜寿命；共享缓存优先考虑 s-maxage，存在 max-age 时优先于 Expires。当前年龄还需考虑 Date、Age 与传输时间，并非每次读缓存都重新计时。

需要验证时发送 If-None-Match（来自 ETag）或 If-Modified-Since（来自 Last-Modified）。对于 GET，验证未变化可返回 304，更新元数据并复用已存正文；变化则通常返回 200 和新正文。缺少验证器时可能只能重新下载。

| 响应指令 | 含义 |
| --- | --- |
| no-cache | 允许存储；无字段参数时，复用前必须成功验证 |
| no-store | 不得存储该响应及相关请求信息；不是删除全部旧缓存的命令 |
| private | 不允许共享缓存存储，浏览器私有缓存仍可存储 |
| public | 显式允许缓存，仍需遵守其他缓存条件 |
| max-age=0 | 立即陈旧，不等同于绝不存储 |
| must-revalidate | 陈旧后复用必须成功验证，不能随意用旧响应 |

如含哈希的静态资源可设置长 max-age 加 immutable；HTML 可用 no-cache 配合 ETag。敏感响应按需要设置 no-store；private 只限定存储位置，并不等于内容加密。规范依据：[RFC 9111 §4、§5](https://www.rfc-editor.org/rfc/rfc9111.html)。

## 适用边界与易错点

no-cache 允许存储但复用前需验证；no-store 禁止存储。个性化响应不可误放共享缓存。发布新版本时保留旧资源，防止已打开页面后续加载旧 chunk 失败。

## 参考资料

- [MDN：HTTP 缓存](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Caching)

## 关联题目

- [如何系统优化首屏、请求、渲染和打包性能？](../../questions/frameworks-tools/q-c374ef0f-frontend-optimization.md)
- [如何实施前端灰度发布？](../../questions/system-design/q-5237f1de-frontend-canary.md)
- [HTTP 强缓存、协商缓存、no-cache 与 no-store 有何区别？](../../questions/networks/q-e7b9f16e-http-cache-validation.md)
