# 2026-09-22 前端、网络与工程面试题目输入

状态：已处理。来源：用户在本任务中提供的 26 项题目及草稿；未提供公司、岗位、面试日期或个人项目经历。

## 原始输入与题目映射

以下保留原题意，仅整理空白和长段落。每项链接到可独立阅读的标准题目；call/apply 与 bind 拆为两道题。

| 原始题意 | 整理后题目 |
| --- | --- |
| https在劫持之后为什么能不被篡改 | [HTTPS 遭遇网络劫持后，为什么能发现篡改？](../questions/security/q-65905378-https-hijacking.md) |
| tcpip协议干什么用 | [TCP/IP 协议族用来解决什么问题？](../questions/networks/q-3c04d3b9-tcp-ip-purpose.md) |
| udp适用场景 | [UDP 适用于哪些场景，如何处理可靠性？](../questions/networks/q-00344f12-udp-scenarios.md) |
| http缓存机制、nocatch和nostore、协商缓存 | [HTTP 强缓存、协商缓存、no-cache 与 no-store 有何区别？](../questions/networks/q-e7b9f16e-http-cache-validation.md) |
| git用哪些命令比较多 | [常用 Git 命令有哪些，如何组织日常协作？](../questions/frameworks-tools/q-c90ba134-git-common-commands.md) |
| 节流和防抖 | [节流和防抖有什么区别，如何实现？](../questions/programming-languages/q-5019bf5f-debounce-throttle.md) |
| 服务器限制上传数量怎么实现 | [服务器如何限制上传文件数量、并发与频率？](../questions/system-design/q-a86f1bde-upload-limits.md) |
| 直播比赛如何实时加载评论 | [直播比赛中如何实时加载评论？](../questions/system-design/q-ff51ab3c-live-comments.md) |
| 主动推送涉及前端什么技术 | [服务端主动推送涉及哪些前端技术？](../questions/networks/q-ee9b8206-server-push-options.md) |
| 长轮询 | [长轮询如何工作，有哪些代价？](../questions/networks/q-b6f6c709-long-polling.md) |
| 讲一个你做的比较满意的项目，说明你在项目中的项目背景、产出贡献和亮点 | [如何介绍最满意的项目背景、个人贡献与亮点？](../questions/software-engineering/q-fcc28b80-project-contribution.md) |
| TypeScript中箭头函数和普通函数有什么区别 | [TypeScript 中箭头函数和普通函数有什么区别？](../questions/programming-languages/q-7d15739a-arrow-ordinary-function.md) |
| TypeScript中的 any 和 unknown 两个类型有什么区别 | [TypeScript 的 any 和 unknown 有什么区别？](../questions/programming-languages/q-a15bc115-any-vs-unknown.md) |
| 跨专业基于什么动机 | [如何说明跨专业进入技术岗位的动机？](../questions/software-engineering/q-88585ca3-cross-major-motivation.md) |
| 和mentor有过意见分歧吗，如何处理 | [与 mentor 有技术分歧时，如何处理？](../questions/software-engineering/q-ca1234e1-mentor-disagreement.md) |
| 一个非常陌生之前没接触过的技术模块或项目，怎么从0到1开始开展 | [面对陌生技术模块，如何从 0 到 1 开展？](../questions/software-engineering/q-dba9aff0-unfamiliar-module.md) |
| 什么是盒模型 解释一下box-sizing属性 | [什么是 CSS 盒模型，box-sizing 如何影响尺寸？](../questions/frameworks-tools/q-a9e0dcb1-box-sizing.md) |
| 解释== 和 ===的区别，[0] == [0]和[0] === [0]的输出分别是 | [== 与 === 有何区别，两个 [0] 的比较结果是什么？](../questions/programming-languages/q-26a70cc5-array-equality.md) |
| monorepo相较于multirepo的好处，monorepo各种解决方案的区别，为啥不用npm workspace | [Monorepo 相比 Multirepo 有何取舍，为什么不直接用 npm workspaces？](../questions/software-engineering/q-6c28751d-monorepo-vs-multirepo.md) |
| SSR和CSR的优缺点，resumable ssr是什么。首屏加载哪个快，能够交互哪个快。SSR有哪些不太好处理的问题。 | [SSR、CSR 与 Resumable SSR 有何区别，首屏与交互谁更快？](../questions/frameworks-tools/q-1c7fbfdd-ssr-csr-resumability.md) |
| 用户登录实现方方案cookie, session, token的区别 | [Cookie、Session、Token 如何配合实现登录？](../questions/security/q-d2f71611-cookie-session-token.md) |
| 手撕eventEmitter on call off的实现 | [如何实现 EventEmitter 的 on、call 和 off？](../questions/programming-languages/q-836204b0-event-emitter.md) |
| 手撕call/apply实现bind | [如何手写 call 和 apply，临时属性法有哪些限制？](../questions/programming-languages/q-3b0f0c9c-call-apply.md)；[如何使用 call/apply 实现 bind，并处理 new？](../questions/programming-languages/q-9b1b88a0-bind-with-apply.md) |
| 执行 new MyQueue() 时的创建对象、关联原型、绑定 this、执行函数和默认返回对象；this.p = [] 在新对象上创建 p 属性。 | [new MyQueue() 做了什么，this.p = [] 存在哪里？](../questions/programming-languages/q-9e2a6796-new-constructor.md) |
| webworker最多能有几个 worker ,线程间如何通信 | [Web Worker 最多能创建几个，线程间如何通信？](../questions/frameworks-tools/q-88b02c0b-worker-limits-messaging.md) |
| 大屏项目中性能优化的方法 | [大屏项目如何进行持续运行的性能优化？](../questions/frameworks-tools/q-f93a75ec-dashboard-performance.md) |

## new 草稿原文

执行 `new MyQueue()` 时，JavaScript 会：

1. 创建一个新对象。
2. 将它的原型关联到 `MyQueue.prototype`。
3. 让函数内部的 `this` 指向这个新对象，并执行函数。
4. 默认返回这个对象。

所以 `this.p = []` 就是在新对象上创建 `p` 属性。

整理时补充：普通构造函数显式返回对象或函数时会替换默认实例；每次构造的数组与原型上的共享数组也需区分。

## 整理说明

- 新增 27 道题、15 个知识点，复用并扩展 HTTP 缓存、登录认证、CSS 盒模型等已有内容，未重复创建同义知识页。
- “nocatch、nostore”规范为 `no-cache`、`no-store`；EventEmitter 的 call 按事件触发方法处理。
- “上传数量”未指定口径，分别解释单次文件数、累计配额、并发和频率，未假定真实服务器的限制。
- HTTPS 说明网络控制与信任根失陷的区别；Worker 数量、SSR 性能均避免固定或绝对化结论。
- 行为题提供回答结构和待填写示例，未虚构用户项目、转专业动机或 mentor 分歧。
- 手写示例明确策略和约束：仅尾触发防抖、仅首触发节流、受限临时属性调用、非完整 bind polyfill。
- 技术资料来自 RFC、语言与浏览器标准及工具官方文档，见相应知识页的链接。ready 表示内容已整理，不表示人工复核。

## 检查记录

- 全库共 65 道题、41 个知识点；检查 106 个条目的 ID 唯一性、必填元数据、标题、路径、关系类型与目标、反向链接、分类索引数量和前置依赖无环，检查所有 Markdown 本地链接。
- 从题目页提取 JavaScript 示例，在 Node.js 22.16.0 中完成 8 组行为检查：EventEmitter、call/apply、bind、防抖/节流、相等比较和 new 的实例隔离；定时器使用确定性模拟时钟。
- TypeScript 5.8.3 strict/noEmit 检查 any/unknown 示例及预期报错断言，并运行 readName 的输入验证。
- 真实浏览器、网络代理、服务端多实例配额及性能压测未执行；场景题为方案分析，不把示例检查视为生产集成验证。
