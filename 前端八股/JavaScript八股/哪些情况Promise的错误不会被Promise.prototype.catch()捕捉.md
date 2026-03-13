---
Date: 2026-03-13
upstream: "[[Promise]]"
related: 相关卡1
tags:
---
1. 宏任务中的错误
如果在`setTimeOut/setInterval/事件回调`等宏任务中抛出错误，Promise的catch无法捕获这类错误
Promise的catch只能监听自己微任务链中的错误，对宏任务里的错误无法捕获

2. 状态已定型
Promise的状态一旦变为`fulfilled/rejected`，就永远无法修改，如果错误发生在状态定型后，catch无法捕获

3. 错误在中途被拦截
如果在 `.catch` 之前，已经在某个 `.then` 的第二个参数（`onRejected`）中处理了错误，且没有在其中再次抛出异常，那么错误就会在这一层被捕获，后续的 `catch` 就收不到任何信号。

4. 断开的Promise链
Promise 的`catch`是 “链式捕获”，依赖完整的 Promise 链；如果链中某个`then`里返回的 Promise 没有被`return`，就会导致链断裂


