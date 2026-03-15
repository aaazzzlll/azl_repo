---
Date: 2026-03-15
upstream: " 父卡片"
related: "[[Object.defineProperty和Proxy的区别]]"
tags:
---
# 响应式实现
**Vue 2**
	使用Object.defineProperty只能劫持单个属性，所以新增/删除属性、修改数组下标都没响应，性能一般

**Vue 3**
	Proxy代理整个对象，所有操作都能监听到，性能更好

# API风格
**Vue 2**
	选项式API：逻辑分散，数据写在 `data`，方法写在 `methods`，计算属性写在 `computed`，监听写在 `watch`

**Vue 3**
	组合式API：逻辑聚合，以setup为入口，通过 `reactive/ref` 声明响应式数据，`computed/watch` 作为函数导入使用


# 性能优化
**Vue 2**
	

**Vue 3**
	


# 体积&构建
**Vue 2**
	因为全局 API 无法Tree-shaking，打包体积大

**Vue 3**
	采用模块化设计，所有 API 按需导入，Tree-shaking 更彻底，打包体积更小，而且适配 Vite 等工具，构建速度也更快

