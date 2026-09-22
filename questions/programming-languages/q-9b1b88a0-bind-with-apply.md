---
id: "q-9b1b88a0"
title: "如何使用 call/apply 实现 bind，并处理 new？"
category: "programming-languages"
tags: ["JavaScript"]
status: "ready"
type: "coding"
created: "2026-09-22"
updated: "2026-09-22"
scope: ["允许原生 apply、Reflect.construct；核心语义演示而非完整 polyfill"]
relations:
  examines: ["k-02569c54"]
---

# 如何使用 call/apply 实现 bind，并处理 new？

## 题目

用 apply 实现保存 this 和前置参数的 bind；讨论绑定函数被 new 调用的行为。

## 简要回答

bind 返回闭包，普通调用合并前后参数并用 apply 调用目标；构造调用忽略绑定接收者，并使用 Reflect.construct 保留目标构造及显式对象返回值。不能只写一个箭头包装，因为它不能 new。

## 约束与实现

输入为函数、任意接收者和前置参数；输出包装函数。允许使用原生 apply 和 Reflect.construct，现代 JavaScript。本实现展示核心行为，不是完整 bind polyfill。

```js
function myBind(fn, receiver, ...preset) {
  if (typeof fn !== 'function') throw new TypeError('fn must be a function');
  function bound(...later) {
    const args = [...preset, ...later];
    if (new.target) {
      return Reflect.construct(
        fn, args, new.target === bound ? fn : new.target
      );
    }
    return fn.apply(receiver, args);
  }
  return bound;
}
```

```js
function Point(x, y) { this.x = x; this.y = y; }
const BoundPoint = myBind(Point, { ignored: true }, 2);
const p = new BoundPoint(3);
console.log(p.x, p.y, p instanceof Point); // 2 3 true
const sum = myBind(function(a, b) { return this.n + a + b; }, { n: 10 }, 1);
console.log(sum(2)); // 13
```

## 分析与边界

原生绑定函数的构造能力跟随目标，且拥有特殊内部语义。本包装器自身总有构造能力：目标为箭头时 new 会在 Reflect.construct 抛错；prototype、instanceof bound、name、length、继承与 newTarget 检测也不完全等价。示例 p instanceof BoundPoint 为 false，原生 bind 的对应结果通常为 true。若面试要求只支持普通调用，可移除 new 分支，明确不支持构造即可。

## 复杂度与边界情况

每次调用复制 m+n 个参数，时间及额外空间 O(m+n)，绑定时保留 m 个参数；不含目标执行。验证参数预置、严格 this、构造器显式返回对象、class 构造、箭头构造失败与异常透传。

## 相关知识点

- [函数调用、this 绑定与构造语义](../../knowledge/programming-languages/k-02569c54-function-this-new.md)

## 示例验证

在 Node.js 22.16.0 中验证严格模式接收者、预置参数、构造器返回对象/原始值、class、箭头构造失败和错误传播，并确认了文中 instanceof 包装函数的差异。

## 题目来源

- [用户输入与整理记录](../../inbox/2026-09-22-frontend-network-engineering.md)
