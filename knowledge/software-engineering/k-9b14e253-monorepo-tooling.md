---
id: "k-9b14e253"
title: "Monorepo 依赖管理与任务编排"
category: "software-engineering"
tags: ["工程化","Monorepo"]
status: "ready"
created: "2026-09-22"
updated: "2026-09-22"
scope: ["工具能力按 2026-09-22 官方资料整理；安装和发布策略取决于配置"]
---

# Monorepo 依赖管理与任务编排

## 核心概念

Monorepo 将多个应用或包放入同一版本库；Multirepo 把它们分开。仓库布局、包安装和任务调度是三个不同层次，选了 Monorepo 不意味着必须统一部署或统一版本号。

## 原理与机制

统一仓库能在同一个提交中修改应用与共享库，共用检查规则并发现受影响项目；代价是权限隔离较粗、依赖耦合和 CI 规模更大。包管理器的 workspace 负责识别本地包、安装依赖与链接；任务编排工具利用依赖图决定顺序、并行任务和复用缓存。

| 工具层 | 典型能力 |
| --- | --- |
| npm workspaces | 自动链接工作区包，选择工作区运行脚本 |
| pnpm workspace | workspace 协议、本地包引用与依赖安装布局，支持过滤 |
| Yarn workspaces | 工作区与 workspace 协议；安装策略随版本和配置变化 |
| Turborepo | 围绕工作区脚本配置任务依赖、并行与结果缓存，可逐步加入已有工程 |
| Nx | 除任务编排与缓存外，还提供项目图、受影响分析、插件、生成器与模块边界治理 |
| Changesets | 声明包的变更级别，协调版本、changelog 和发布 |
| Lerna | 多包运行与版本发布；v6+ 将任务调度委托给 Nx，不应只把它当旧式安装工具 |

## 适用边界与易错点

有 workspace 不等于有跨项目构建结果缓存，也不等于自动只构建受影响项目。缓存要正确声明输入、环境变量、输出和依赖，否则可能拿到过期结果。不能以“npm 不支持 Monorepo”为理由排除 npm，需用实际规模、安装与 CI 测量证明选型收益。

## 参考资料

- [npm v11：workspaces](https://docs.npmjs.com/cli/v11/using-npm/workspaces/)
- [pnpm：workspace](https://pnpm.io/workspaces)
- [Nx：任务结果缓存](https://nx.dev/docs/features/cache-task-results)
- [Nx：能力概览](https://nx.dev/docs/getting-started/intro)
- [Yarn：workspaces](https://yarnpkg.com/features/workspaces)
- [Turborepo 官方仓库](https://github.com/vercel/turborepo)
- [Changesets：版本与发布](https://changesets-docs.vercel.app/)
- [Lerna：任务调度与发布](https://lerna.js.org/docs/introduction)

## 关联题目

- [Monorepo 相比 Multirepo 有何取舍，为什么不直接用 npm workspaces？](../../questions/software-engineering/q-6c28751d-monorepo-vs-multirepo.md)
