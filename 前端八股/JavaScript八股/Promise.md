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
	3. `Promise.all()` - 所有 Promise 都成功时返回一个包含所有兑现值的数组，返回的也是一个Promise
	4. `Promise.race()` - 第一个完成的 Promise 的结果
	5. `Promise.allSettled()` - 所有 Promise 完成后返回结果
	6. `Promise.prototype.then()` - 添加成功回调
	7. `Promise.prototype.catch()` - 添加失败回调
	8. `Promise.prototype.finally()` - 无论成功失败都执行

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