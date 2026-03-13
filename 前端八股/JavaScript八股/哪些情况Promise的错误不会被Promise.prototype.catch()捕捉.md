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

4. 断开的Promise链



怎么优化渲染过程这些指标  