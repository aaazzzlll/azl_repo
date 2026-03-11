---
Date: 2026-03-11
upstream: " 父卡片"
related: 相关卡1
tags:
---
**Vue 3生命周期分4大阶段（创建，挂载，更新，卸载）**
`<script setup>`的代码执行时机等同于beforeCreate+created

### 创建
初始化组件数据，配置
可操作内容：初始化数据、调用接口，但无法操作DOM
#### setup



### 挂载
将组件渲染到DOM中
可操作内容：操作DOM，初始化第三方库
#### 1.onBeforeMount
模板编译完成，未挂载DOM
#### 2.onMounted
操作DOM、初始化第三方库

### 更新
响应式数据变化，重新渲染组件
可操作内容：监听数据变化后的DOM调整
#### 1.onBeforeUpdate
获取更新前的DOM状态
#### 2.onUpdated
调整更新后的DOM

### 卸载
清理组件资源，避免内存泄漏
可操作内容：清楚定时器、取消事件监听、解绑全局事件
#### 1.onBeforeUnmount
清理定时器、取消事件监听
#### 2.onUnmounted
解绑全局事件、销毁第三方库实例
