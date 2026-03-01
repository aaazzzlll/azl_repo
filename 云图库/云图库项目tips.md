以后写代码，遇到下面这三种数据源，**无脑**上 `computed`，绝对不出错：

1. **来自 `props` 的数据**
    
    - 父组件传下来的 `props.id` 可能会变，如果你在子组件里写 `const localId = props.id`，你就断开了连接。
    - ✅ `const localId = computed(() => props.id)`
2. **来自 `route` (路由) 的数据**
    
    - URL 是整个网页最核心的可变状态。
    - ✅ `const id = computed(() => route.params.id)`
3. **来自 `Store` (Pinia/Vuex) 的数据**
    
    - 全局状态随时可能被别的组件改掉。
    - ✅ `const user = computed(() => userStore.userInfo)`


在实现图片裁剪功能的时候，新增了扩展功能，用户可以自行选择自由裁剪或者固定的裁剪比例。但是在实现的时候这个组件库有一些小问题，修改选项的时候裁剪框没有同步更新。为了解决这个问题，我使用了watch监视aspectRatio，一旦被选中的选项变化，就判断选择的是不是自由比例，如果不是就强制刷新裁剪框配置。
在最后项目收尾时，发现用户选择裁剪比例有延迟（例如用户先点击4:3，再点击1:1，此时显示的是4:3)，为了解决这个问题使用nextTick


在实现AI扩图功能的时候，图片不能过大或者过小，否则AI无法完成扩图任务。
在开发这个功能的时候，首先是由前端向后端提出创建任务请求，后端再去向服务器请求扩图，在等待过程中，前端每隔3秒会向后端轮询一次，直到任务状态为SUCCEEDED或者FAILED
**注意：在任务完成之后，无论是成功还是失败都必须关闭定时器**


Vue默认会复用组件实例，当从/space/1跳转到/space/2时，因为这两个路径使用的是同一个组件，Vue为了节省性能，不会销毁旧的组件再重新创建一个组件。所以需要再SpaceDetailPage添加watch，监听空间id的变化


在开发协同编辑模块的时候，使用的是[webSocket](../前端八股/webSocket.md)
在项目中使用WebSocket 的完整步骤总结（6 步走）：
	1. 明确需求：确认要服务器主动推送
	2. 后端准备：提供ws地址(wss:// 最好)
	3. 前端创建连接：new WebSocket(url)或封装类
	4. 监听事件：onopen/onmessage/onclose/onerror
	5. 发送消息：ws.send()
	6. 处理断连&清理：