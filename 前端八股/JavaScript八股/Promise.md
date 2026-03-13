---
Date: 2026-03-08
upstream: "[[../JavaScript八股/异步方案|异步方案]]"
related: "[[../手写/手写题|手写题]]"
tags:
  - Promise
---
**Promise是异步编程的解决方案，表示一个异步操作的最终完成或失败**

**状态**：
	pending：初始状态
	fulfilled：操作成功完成
	rejected：操作失败

**方法**：
	1. `Promise.resolve()` - 返回一个 resolved 状态的 Promise
	2. `Promise.reject()` - 返回一个 rejected 状态的 Promise
	3. `Promise.all()` - 并行执行多个 Promise，全部成功返回结果数组（顺序和输入一致），任意一个失败立即返回第一个失败原因
	4. `Promise.race()` - 多个 Promise 竞速，返回第一个完成（成功 / 失败）的 Promise 结果
	5. `Promise.allSettled()` - 等待所有 Promise 完成（无论成功 / 失败），返回每个 Promise 的状态和结果
	6. `Promise.any()`- 多个 Promise 中返回第一个成功的结果，全部失败则抛出 AggregateError
	7. `Promise.prototype.then()` - 添加成功回调
	8. `Promise.prototype.catch()` - 添加失败回调
	9. `Promise.prototype.finally()` - 无论成功失败都执行

```javascript
Promise.allSettled([
  Promise.resolve(33),
  new Promise((resolve) => setTimeout(() => resolve(66), 0)),
  99,
  Promise.reject(new Error("一个错误")),
]).then((values) => console.log(values));

// [
//   { status: 'fulfilled', value: 33 },
//   { status: 'fulfilled', value: 66 },
//   { status: 'fulfilled', value: 99 },
//   { status: 'rejected', reason: Error: 一个错误 }
// ]
```

JS 原生 Promise 实例的核心属性：
1. **`[[PromiseState]]`（内部状态）**：不可直接访问，值为 `pending`/`fulfilled`/`rejected`，状态不可逆；
2. **`[[PromiseResult]]`（结果值）**：不可直接访问，`fulfilled` 时存成功结果，`rejected` 时存失败原因；
3. **原型方法**：`then()`/`catch()`/`finally()`（用于注册回调）；
4. **静态方法**：`Promise.resolve()`/`Promise.reject()`/`Promise.all()` 等（挂载在 Promise 构造函数上）。