---
Date: 2026-03-13
upstream: " 父卡片"
related: 相关卡1
tags:
---
**try/catch只能捕获同步代码执行过程中抛出的错误**

1. try/catch无法捕获普通的Promise错误
因为Promise的错误是异步的，当Promise
```javascript
try{
	new Promise((resolve,reject)=>{
		reject(new Error("error"))
	})
}catch(err){
	console.log("捕获到错误：",err)//不会执行这一行
}
```