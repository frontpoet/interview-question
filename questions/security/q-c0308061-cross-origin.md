---
id: "q-c0308061"
title: "什么是跨域，常用解决方式有哪些？"
category: "security"
tags: ["浏览器","HTTP","安全"]
status: "ready"
type: "concept"
created: "2026-09-10"
updated: "2026-09-10"
relations:
  examines: ["k-ac6de39b"]
---

# 什么是跨域，常用解决方式有哪些？

## 题目

解释同源策略、预检、凭证请求和代理方案。

## 简要回答

协议、主机或端口任一不同即跨源，跨源不等于跨站。常用方案是服务端正确配置 CORS，或通过受控同源网关转发。开发代理只解决开发环境，不自动解决生产部署。

服务端按白名单返回 Access-Control-Allow-Origin；预检允许所需方法和头。带 Cookie 时客户端启用 credentials，服务端允许凭证且不能把 Origin 设为 `*`。动态 Origin 响应需考虑 `Vary: Origin`。

JSONP 只适合受限的历史 GET 场景且有脚本执行风险；no-cors 不会让 JS 得到可读响应。不要靠禁用浏览器安全或公共代理解决业务跨域。CORS 也不能替代鉴权和 CSRF 防护。

## 相关知识点

- [同源策略与 CORS](../../knowledge/security/k-ac6de39b-cors.md)

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-10-frontend-and-os.md)
