---
id: "q-cb7496a6"
title: "如何实现前端路由，Hash 和 History 有何区别？"
category: "frameworks-tools"
tags: ["浏览器","JavaScript"]
status: "ready"
type: "principle"
created: "2026-09-10"
updated: "2026-09-10"
scope: ["单页应用，Hash 或 History API"]
relations:
  examines: ["k-afeb85af"]
---

# 如何实现前端路由，Hash 和 History 有何区别？

## 题目

说明路由匹配、主动导航、前进后退和刷新处理。

## 简要回答

路由器读取 URL，匹配路由表并渲染界面。Hash 监听 hashchange，片段不会发送给服务端；History 修改同源路径，监听 popstate 处理历史遍历，深链接刷新需服务端回退。

## 最小 History 示例

约定 render 是同步渲染回调，本例只展示订阅和导航，不包含嵌套路由与完整链接拦截。

```js
function createRouter(render) {
  const sync = () => render(location.pathname + location.search);
  addEventListener('popstate', sync);
  sync();
  return {
    navigate(path, replace = false) {
      const url = new URL(path, location.href);
      if (url.origin !== location.origin) throw new Error('Same-origin URL required');
      history[replace ? 'replaceState' : 'pushState']({}, '', url);
      sync(); // pushState/replaceState 不触发 popstate。
    },
    dispose() { removeEventListener('popstate', sync); }
  };
}
```

拦截链接时保留修饰键、新标签、下载和跨源行为；生产实现还需参数解析、404、权限校验入口、滚动恢复和焦点管理。服务端只对页面路由回退，静态资源/API 错误应保留真实状态。

## 相关知识点

- [浏览器 URL 与前端路由](../../knowledge/frameworks-tools/k-afeb85af-routing.md)

## 示例验证

使用 location/history 事件桩验证主动导航、前进后退同步、跨源拒绝和清理；未在真实浏览器验证服务端回退。

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-10-frontend-and-os.md)
