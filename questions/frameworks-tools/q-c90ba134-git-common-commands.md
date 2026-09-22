---
id: "q-c90ba134"
title: "常用 Git 命令有哪些，如何组织日常协作？"
category: "frameworks-tools"
tags: ["Git","工程化"]
status: "ready"
type: "concept"
created: "2026-09-22"
updated: "2026-09-22"
relations:
  examines: ["k-f2ec3b79"]
---

# 常用 Git 命令有哪些，如何组织日常协作？

## 题目

介绍经常使用的 Git 命令，并说明解决冲突、暂存工作和撤销修改的选择。

## 简要回答

| 目的 | 常用命令 | 关注点 |
| --- | --- | --- |
| 获取仓库与状态 | clone、status、log --oneline --graph、show | 先确认分支和现有改动 |
| 检查与提交 | diff、add -p、diff --cached、commit | 分批提交相关修改 |
| 切分支 | switch -c、switch、branch | 未提交内容可能随切换保留或阻止切换 |
| 同步协作 | fetch、merge、rebase、push | 理解历史变化，按团队约定集成 |
| 临时保存 | stash push -u、stash list、stash apply | -u 包含未跟踪文件；apply 保留 stash |
| 修复与追踪 | restore、revert、cherry-pick、reflog、bisect | 按修改范围和是否共享选择 |

## 分析与边界

典型流程是 status/diff → 建分支 → 修改并验证 → add -p → diff --cached → commit → fetch → 集成远端变更 → push。rebase 冲突时编辑、add 后 rebase --continue，决定放弃则 rebase --abort。revert 产生新提交，不会抹去原提交；reset --hard 会覆盖工作区已跟踪文件，不作为常规撤销首选。

## 相关知识点

- [Git 工作区、暂存区与协作历史](../../knowledge/frameworks-tools/k-f2ec3b79-git-workflow.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-22-frontend-network-engineering.md)

