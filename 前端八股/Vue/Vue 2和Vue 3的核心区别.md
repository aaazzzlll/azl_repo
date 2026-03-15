---
Date: 2026-03-15
upstream: " 父卡片"
related: "[[Object.defineProperty和Proxy的区别]]"
tags:
---
# 响应式实现
**Vue 2**
	使用Object.defineProperty只能劫持单个属性，所以新增/删除属性、修改数组下标都没响应

**Vue 3**
	Proxy代理整个对象，所有操作都能监听到

# API风格
**Vue 2**
	选项式API：按 “功能类型” 拆分代码，数据写在 `data`，方法写在 `methods`，计算属性写在 `computed`，监听写在 `watch`

**Vue 3**
	组合式API：以setup为入口，通过 `reactive/ref` 声明响应式数据，`computed/watch` 作为函数导入使用


# 性能优化
**Vue 2**
	使用Object.defineProperty只能劫持单个属性，所以新增/删除属性、修改数组下标都没响应

**Vue 3**
	Proxy代理整个对象，所有操作都能监听到


# 体积&构建
**Vue 2**
	使用Object.defineProperty只能劫持单个属性，所以新增/删除属性、修改数组下标都没响应

**Vue 3**
	Proxy代理整个对象，所有操作都能监听到

