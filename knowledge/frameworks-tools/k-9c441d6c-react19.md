---
id: "k-9c441d6c"
title: "React 19 的 Actions 与新 API"
category: "frameworks-tools"
tags: ["React","Hooks"]
status: "ready"
created: "2026-09-10"
updated: "2026-09-10"
aliases: ["React 19"]
scope: ["React 19.0 基线；单独注明 19.2 增量，不声称穷举所有 19.x"]
---

# React 19 的 Actions 与新 API

## 核心概念

React 19 增强异步交互、表单和资源读取能力；小版本新增 API 需与 19.0 区分。

## 原理与机制

Actions 配合异步状态转换管理 pending、结果和错误；useActionState 管理 action 状态，useOptimistic 支持乐观展示，useFormStatus 读取所在父表单的提交状态。use 可读取 Promise 或 Context，读取待定 Promise 时与 Suspense 协作。

## 适用边界与易错点

19.0 还支持函数组件接收 ref prop、ref 回调清理和文档元数据等。19.2 新增 Activity、useEffectEvent 等，不能都称为 19.0 功能。React Compiler 的启用与框架集成需另行确认，不等于安装 React 19 后自动开启。

## 参考资料

- [React 19 发布说明](https://react.dev/blog/2024/12/05/react-19)
- [React 19.2 发布说明](https://react.dev/blog/2025/10/01/react-19-2)

## 关联题目

- [React 19 有哪些值得关注的新能力？](../../questions/frameworks-tools/q-be806d53-react-19-features.md)
