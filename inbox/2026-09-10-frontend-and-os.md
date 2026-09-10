# 2026-09-10 前端与操作系统题目输入

状态：已处理。来源：用户在本任务中提供的题目与回答草稿；未提供公司、岗位和面试日期。

以下保留原始题意和草稿，清理了 HTML 空格实体和无意义编号。草稿中可能有错误，以整理后的题目及知识点为准。

## 原始输入

- 串行地执行传入的 promises，实现效果与 promise.all 区别只有“串行执行”。
- CSS 常用什么属性；介绍 display；position 有什么值；absolute 与 fixed 区别、fixed 与 sticky 区别；relative 相对于谁、设置 left 这种属性有用吗；属性居中的方法；animation 和 transition 的区别，transform 属性。
- 为什么 import 一个东西只打包一个东西？Tree shaking。
- 流式对话的输出是怎么实现的？AI 应用一个一个或一行一行输出，后端格式和请求头有何不同？JS 如何接收处理？EventSource 只能 GET，需要 POST 怎么做？
- 为什么选用 SQLite，了解 IndexedDB 吗，为什么不用 IndexedDB？
  - 数据结构比较复杂、索引能力成熟、事务能力强、不希望存储层绑定浏览器，客户端/Node 环境也能用。SQLite 可以直接写 SQL。
  - IndexedDB 适合纯浏览器应用；纯 Web、无需复杂表关联、主要保存缓存、离线数据、草稿、文件，希望使用浏览器原生能力时优先考虑。
- 骨架屏如何实现？页面组件很多，如何在页面资源全加载完前展示接近真实界面的骨架？
  - 尽量约定图片等内容的宽高；不同类型设计不同 skeleton；Skeleton 和真实组件共用 Layout，避免页面抖动；先真实文字加图片骨架，图片完成后替换。
- 性能优化的指标？如何检测 LCP？不埋点自动化怎么做？Performance 面板什么用，录制哪些数据？
- 虚拟列表实现与原理。
- *进程之间通信方式。
- *进程和线程区别。
- 实现前端路由，Hash 和 History 的区别。
- 浏览器渲染原理。
- 性能优化方式：首屏、网络加载、重排重绘、打包。
- 大文件分片上传。
- 前端灰度发布方案。
- 设计前端异常监控系统。
- 跨域概念及解决跨域。
- 浏览器存储、Cookie、Token。
- 登录安全最佳实践。
- React 组件更新流程：
  - 点击执行事件函数；setState 放入队列（原文“但并非不是直接修改当前变量”），批处理；Render 再调用组件得到 React Element；Reconciliation 比较新旧虚拟 DOM、计算 diff；Commit 修改 DOM；DOM 更新后先 useLayoutEffect，再浏览器绘制。
- useEffect 和 useLayoutEffect：
  - useLayoutEffect：DOM 更新但尚未绘制，阻塞绘制。
  - useEffect：通常在浏览器绘制后执行。
  - 原文：“后者主要用于读取 DOM 然后马上修改布局，例如 tooltip。前者可能会出现页面闪烁。”
- 依赖数组触发更新：
  - 原文：“对于基本类型，值相同，使用 Object.is === true 比较对象引用相同，则跳过更新。”
  - 引用类型内容相同也可能触发无效更新。
  - 返回原数组、对象，不要无意义使用 {...obj}、[...arr]；需要稳定引用时用 useMemo/useCallback。
- 实现一个与 useEffect 相同但第一次不执行副作用的 Hook。
- useMemo / useCallback。
- #虚拟 DOM 原理、Fiber 原理。
- React 19 新技术点。

## 整理说明

- * 和 # 仅保留为用户标记，不推断难度或频率。
- Promise 题采用延迟任务函数数组；SQLite 选型保留实际环境待确认；“属性居中”暂按元素居中。
- React 草稿修正状态快照、协调所属阶段、Effect 时机与引用更新规则。
- 原仓库没有题目或知识点；本次均为新增，相关题目复用知识点。


## 题目映射

- [如何串行执行异步任务并按顺序返回结果？](../questions/programming-languages/q-06ed975d-serial-promises.md)
- [CSS 常用属性有哪些，分别解决什么问题？](../questions/frameworks-tools/q-82f696ce-css-properties.md)
- [display 如何影响元素的外部布局和内部布局？](../questions/frameworks-tools/q-ce38d22b-display.md)
- [position 有哪些值，如何选择？](../questions/frameworks-tools/q-4ec68f7a-position-values.md)
- [absolute 与 fixed 有什么区别？](../questions/frameworks-tools/q-60dc83c6-absolute-fixed.md)
- [fixed 与 sticky 有什么区别，sticky 为什么可能不生效？](../questions/frameworks-tools/q-a67dce12-fixed-sticky.md)
- [relative 相对于谁定位，left 是否生效？](../questions/frameworks-tools/q-62312ffd-relative-offset.md)
- [如何用 CSS 实现元素水平和垂直居中？](../questions/frameworks-tools/q-5da460ce-centering.md)
- [animation 与 transition 有什么区别？](../questions/frameworks-tools/q-6954df5e-animation-transition.md)
- [transform 有哪些作用，是否影响布局？](../questions/frameworks-tools/q-12fa6aea-transform.md)
- [为什么具名 import 有时只打包用到的代码？](../questions/frameworks-tools/q-2e345dd1-tree-shaking.md)
- [AI 对话的流式输出如何实现？](../questions/networks/q-caad3cc6-stream-chat.md)
- [EventSource 不支持 POST 时如何接收 SSE？](../questions/networks/q-bf0f9c2d-post-sse.md)
- [本地存储为什么选择 SQLite，而不是 IndexedDB？](../questions/databases/q-4dc59b7e-sqlite-indexeddb.md)
- [如何实现接近真实页面的骨架屏？](../questions/frameworks-tools/q-17617362-skeleton.md)
- [前端性能优化关注哪些指标？](../questions/frameworks-tools/q-284fd89e-performance-metrics.md)
- [如何检测 LCP，能否不改业务代码自动测量？](../questions/frameworks-tools/q-2da36d78-measure-lcp.md)
- [Chrome Performance 面板有什么用，录制哪些数据？](../questions/frameworks-tools/q-7fe5632b-performance-panel.md)
- [虚拟列表如何实现，变高列表如何处理？](../questions/data-structures-algorithms/q-e5d02f9a-virtual-list.md)
- [进程之间有哪些通信方式，如何选择？](../questions/operating-systems/q-aa7d6f0c-ipc-methods.md)
- [进程和线程有什么区别？](../questions/operating-systems/q-182ad9c8-process-thread.md)
- [如何实现前端路由，Hash 和 History 有何区别？](../questions/frameworks-tools/q-cb7496a6-frontend-router.md)
- [浏览器从资源到页面像素经历哪些步骤？](../questions/frameworks-tools/q-c25ddcb6-browser-rendering.md)
- [如何系统优化首屏、请求、渲染和打包性能？](../questions/frameworks-tools/q-c374ef0f-frontend-optimization.md)
- [如何设计大文件分片上传与断点续传？](../questions/system-design/q-602a0ded-chunk-upload.md)
- [如何实施前端灰度发布？](../questions/system-design/q-5237f1de-frontend-canary.md)
- [如何设计前端异常监控系统？](../questions/system-design/q-fdff17bf-frontend-errors.md)
- [什么是跨域，常用解决方式有哪些？](../questions/security/q-c0308061-cross-origin.md)
- [Cookie、Web Storage、IndexedDB 与 Token 有何区别？](../questions/security/q-b7ad08d9-browser-storage.md)
- [Web 登录安全应采取哪些措施？](../questions/security/q-069ffd4d-login-security.md)
- [React 组件从 setState 到显示更新经历哪些步骤？](../questions/frameworks-tools/q-d2f67a35-react-update.md)
- [useEffect 和 useLayoutEffect 有什么区别？](../questions/frameworks-tools/q-bf24550f-effect-layout.md)
- [Hooks 依赖数组如何比较，怎样避免无意义重跑？](../questions/frameworks-tools/q-8725cb37-effect-dependencies.md)
- [如何实现跳过初始挂载的 useUpdateEffect？](../questions/frameworks-tools/q-70a359bf-skip-initial-effect.md)
- [useMemo 和 useCallback 有什么区别，何时使用？](../questions/frameworks-tools/q-d8cd67e7-memo-callback.md)
- [虚拟 DOM 的原理是什么，为什么需要 key？](../questions/frameworks-tools/q-af53944d-virtual-dom.md)
- [React Fiber 如何支持可中断渲染？](../questions/frameworks-tools/q-cafcea45-fiber-principle.md)
- [React 19 有哪些值得关注的新能力？](../questions/frameworks-tools/q-be806d53-react-19-features.md)

## 整理结果与检查

- 新增 38 道题、26 个知识点；36 道题为 ready，2 道题为 draft，未标记人工复核。
- draft：元素居中的原始题意、SQLite 选型的实际运行环境。
- 检查条目 ID、分类、关系目标与类型、反向链接、索引、前置依赖循环和本地链接。
- 在 Node 中运行串行任务、SSE、虚拟范围及隔离的路由/Hook 示例检查；真实浏览器、React、后端和代理集成未验证。
