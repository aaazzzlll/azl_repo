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