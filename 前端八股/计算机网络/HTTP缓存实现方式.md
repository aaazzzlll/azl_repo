---
Date: 2026-03-04
upstream: " 父卡片"
related: 相关卡1
tags:
---
1. 强制缓存
只要浏览器判断缓存没有过期，则直接使用浏览器的本地缓存。
利用以下两个HTTP响应头部字段实现：
	Cache-Control:设置缓存策略，如`no-store`（不缓存）、`max-age`（最大缓存时间）等
	Expires：是一个绝对时间，浏览器在此日期之前不会向服务器发送请求


2. 协商缓存
浏览器在本地缓存过期后，浏览器发送一个带有缓存标记的请求，服务端根据资源是否更新告诉客户端是否可以使用缓存

目前主要有两对“Header”组合来实现这个机制：
	1. **Last-Modified和If-Modified-Since**
	响应头中的Last-Modified：指定资源的最后修改时间
	请求头中的If-Modified-Since：客户端在请求时携带Last-Modified，服务器判断资源是否已被修改，如果未修改返回304
	2. **ETag和If-None-Match**
	响应头中的ETag：唯一标识响应资源，服务器通过返回ETag判断资源是否变化
	请求头中的If-None-Match：客户端在请求时将If-None-Match 值设置为 Etag 的值，服务器判断是否存在差异，如果没有则返回304 Not Modified


协商缓存这两个字段都需要配合强制缓存的Cache-Control来使用，只有在未能命中强制缓存的时候，才能发起带有协商缓存字段的请求