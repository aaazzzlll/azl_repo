---
Date:
upstream: " 父卡片"
related: 相关卡1
tags:
---
`1xx`类：服务器收到请求，需要进一步操作
	100 Continue
`2xx`类：请求处理成功
	200 OK 最常见的成功状态码，表示一切正常，服务器返回的响应头都会有body数据
	204 No Content 也是常见的成功状态码，但响应头没有body数据
	206 Partial Content 应用于HTTP分块下载或断点续传，表示响应返回的body数据是资源的一部分
`3xx`类：客户端请求的资源发生变动，需要客户端用新的URL重新发送请求获取资源，即重定向
	301 Moved Permanently 永久重定向，说明请求的资源已经不存在，需改用新的URL再次访问
	302 Found 临时重定向，说明请求的资源还在，但暂时需要用另一个URL访问
	304 Not Modified 表示资源未修改，客户端可以使用缓存资源
`4xx`类：客户端错误，请求有问题
	400 Bad Request 客户端请求的报文有错误
	403 Forbidden 服务器禁止访问资源
	404 Not Found 表示请求的资源在服务器上不存在或未找到
`5xx`类：客户端请求报文正确，但服务器处理时内部发生错误
	500 Internal Server Error 
	501 Not Implemented 表示客户端请求的功能还不支持
	502 Bad Gateway
