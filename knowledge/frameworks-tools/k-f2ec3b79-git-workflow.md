---
id: "k-f2ec3b79"
title: "Git 工作区、暂存区与协作历史"
category: "frameworks-tools"
tags: ["Git","工程化"]
status: "ready"
created: "2026-09-22"
updated: "2026-09-22"
---

# Git 工作区、暂存区与协作历史

## 核心概念

工作区保存当前文件，暂存区保存下次提交的内容，提交形成历史图；分支指向提交。远端跟踪分支是最近获知的远端状态，并非实时远端。

## 原理与机制

编辑后用 diff 看工作区与暂存区差异，add 选择内容，diff --cached 检查待提交快照，commit 记录快照。fetch 获取远端对象和引用，再选择 merge 或 rebase 集成。merge 保留分叉关系，rebase 重放提交并改变提交 ID。

restore 通常恢复文件或暂存状态；reset 移动分支并可修改暂存区/工作区；revert 创建逆向提交，适合撤销共享历史中的修改。reflog 记录本地引用移动，可辅助找回误操作，但不是长期备份。

## 适用边界与易错点

pull 的行为取决于配置与选项，不应总等同于 fetch + merge。不要在不理解结果时用 reset --hard 或强推；共享分支通常优先 revert。冲突需理解双方意图、编辑合并并验证，再 add 和 continue；保留冲突标记并不能解决问题。

## 参考资料

- [Git 官方命令索引与手册](https://git-scm.com/docs/git)

## 关联题目

- [常用 Git 命令有哪些，如何组织日常协作？](../../questions/frameworks-tools/q-c90ba134-git-common-commands.md)

