---
id: "k-afeb85af"
title: "浏览器 URL 与前端路由"
category: "frameworks-tools"
tags: ["浏览器","JavaScript"]
status: "ready"
created: "2026-09-10"
updated: "2026-09-10"
aliases: ["Hash 路由","History 路由"]
scope: ["单页应用，Hash 或 History API"]
---

# 浏览器 URL 与前端路由

## 核心概念

前端路由将 URL 映射到界面，并同步导航与历史记录。

## 原理与机制

Hash 读取 location.hash，监听 hashchange；片段不随 HTTP 请求发送。History 使用 pushState/replaceState 修改同源 URL，应用主动渲染；用户前进后退时通过 popstate 同步界面。

## 适用边界与易错点

pushState 不自动触发 popstate。History 深链接刷新需要服务端对页面路径回退到入口，API 和静态文件不能无差别回退。路由还需处理参数、404、焦点、滚动恢复和链接默认行为。

## 参考资料

- [MDN：History API](https://developer.mozilla.org/en-US/docs/Web/API/History_API/Working_with_the_History_API)

## 关联题目

- [如何实现前端路由，Hash 和 History 有何区别？](../../questions/frameworks-tools/q-cb7496a6-frontend-router.md)
