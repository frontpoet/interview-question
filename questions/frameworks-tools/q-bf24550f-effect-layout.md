---
id: "q-bf24550f"
title: "useEffect 和 useLayoutEffect 有什么区别？"
category: "frameworks-tools"
tags: ["React","Hooks"]
status: "ready"
type: "comparison"
created: "2026-09-10"
updated: "2026-09-10"
scope: ["React 18/19 客户端 Effects；开发 StrictMode 可能重放"]
relations:
  examines: ["k-486fa8e9"]
  follow_up_to: ["q-d2f67a35"]
---

# useEffect 和 useLayoutEffect 有什么区别？

## 题目

比较执行时机、绘制影响和典型用途。

## 简要回答

| 维度 | useEffect | useLayoutEffect |
| --- | --- | --- |
| 时机 | 提交后，通常允许先绘制，但非绝对 | 相关 DOM 更新后、浏览器绘制前 |
| 用途 | 订阅、网络同步、外部系统连接 | 读取布局并同步修正，如 tooltip 定位 |
| 绘制影响 | 不作为绘制后执行的保证 | 会阻塞绘制，应尽量短 |

两者依赖变化时都会先清理旧 Effect，再执行新 setup，卸载时清理；均不在 SSR 中执行。开发 StrictMode 可额外重放。

## 分析与边界

用户原记录的“后者用于读 DOM 并改布局”对应 useLayoutEffect。若用普通 Effect 定位浮层，可能先显示错误位置再修正；Layout Effect 则可在绘制前完成。交互触发的普通 Effect，以及 Layout Effect 中触发的更新，可能让普通 Effect 提前执行。

## 相关知识点

- [React Effect 生命周期](../../knowledge/frameworks-tools/k-486fa8e9-effects.md)

## 原题目

- [React 组件从 setState 到显示更新经历哪些步骤？](q-d2f67a35-react-update.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-10-frontend-and-os.md)
