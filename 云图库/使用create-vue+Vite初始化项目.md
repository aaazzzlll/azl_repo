1. **create-vue是什么**
create-vue是Vue 3官方推荐的轻量级脚手架，通过它可以生成基于Vite的Vue 3项目模板
相比Vue CLi基于Webpack，create-vue基于Vite，项目启动速度提升10倍以上
我通过create-vue初始化项目骨架，根据业务需求选择了TypeScript、Vue Router、Pinia等核心依赖


2. **Vite核心优势（为什么用Vite而不是Webpack）**
	Vite利用浏览器原生ESM，冷启动快
	Vite热更新快，只更新变更模块，调试样式/组件更流畅
	Vite配置简单，默认配置开箱即用，配置维护成本低
3. **企业级前端模板包含什么**
	基础设施：封装了BasicLayout组件，配置了路由，将全局权限校验封装到access.ts文件中，封装了Axios，添加了请求拦截器和响应拦截器（拦截未登录用户使用需要登录的功能）
	通用组件：基于Ant Design Vue二次封装了PictureList组件，用于展示图片列表
	业务组件：针对图片模块业务，我封装了很多组件，比如图片上传组件（包括本地上传组件和URL上传组件），图片编辑组件（使用了vue-cropper组件库）
	工具函数：封装了格式化文件大小的函数、下载图片函数、自定义WebSocket封装，支持事件订阅模式
4. **动态导航菜单怎么实现的**
	前端进行身份校验，