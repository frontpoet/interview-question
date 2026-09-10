---
id: "q-be806d53"
title: "React 19 有哪些值得关注的新能力？"
category: "frameworks-tools"
tags: ["React","Hooks"]
status: "ready"
type: "concept"
created: "2026-09-10"
updated: "2026-09-10"
scope: ["以 React 19.0 为基线，补充 19.2；不将所有 19.x 能力混为 19.0"]
relations:
  examines: ["k-9c441d6c","k-486fa8e9"]
---

# React 19 有哪些值得关注的新能力？

## 题目

按解决的问题介绍主要 API，并明确版本边界。

## 简要回答

- Actions 与 useActionState：组织异步提交、结果、pending 和错误；表单可结合 action 与 useFormStatus。
- useOptimistic：先展示预期结果，再按真实结果协调，仍需失败恢复设计。
- use：在渲染中读取 Promise 或 Context，可与 Suspense/错误边界协作；不要每次客户端渲染随意新建 Promise。
- ref 作为函数组件 prop、ref 回调清理、文档元数据和资源加载相关支持，减少部分手工接线。
- 19.2 增量包括 Activity、useEffectEvent 等；Effect Event 用于 Effect 内非响应式逻辑，不是省略依赖的通用手段。

## 分析与边界

React Compiler 需单独配置或由框架启用，升级 React 19 不等于自动开启。Server Components 及 Server Functions 还涉及框架/构建支持；React 本身不替服务端执行鉴权。回答应给出采用的版本，不能把“新 API”理解成应无差别替换现有代码。

## 相关知识点

- [React 19 的 Actions 与新 API](../../knowledge/frameworks-tools/k-9c441d6c-react19.md)
- [React Effect 生命周期](../../knowledge/frameworks-tools/k-486fa8e9-effects.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-10-frontend-and-os.md)
