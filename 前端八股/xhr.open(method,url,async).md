xhr.open()方法初始化一个新创建的请求，或重新初始化一个请求
method：请求方法
url：要请求的后端地址
async：一个可选的布尔值，表示是否异步执行操作，true表示异步请求，不会阻塞主线程


这个方法是在告诉浏览器：“我要发一个什么方法的请求（GET/POST/...），目标地址是这个 url，这次请求是异步还是同步（true/false）。”

具体完成了以下任务：
- 设置请求方法（method）：GET、POST、PUT、DELETE 等
- 设置目标 URL
- 设置是否异步（true = 异步，不会阻塞页面；false = 同步，会卡住页面 —— 现在基本不用 false）
- **重置 XMLHttpRequest 对象的内部状态**，让它进入“可以配置”的状态
- 为后续的 setRequestHeader、onload、send 等操作做准备

如果没有open就不能设置请求头、设置事件监听