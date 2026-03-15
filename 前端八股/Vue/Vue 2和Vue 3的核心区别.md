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

1. 虚拟DOM和Diff算法优化
	**Vue 2**：Vue 2的虚拟DOM是全量对比，每次更新都要遍历整个虚拟DOM树
	**Vue 3**：Vue 3在编译阶段给节点打静态标记，运行时只对比带标记的动态节点，跳过所有静态内容，Diff 效率大幅提升
2. 响应式优化
	Vue3 的响应式从 Object.defineProperty 改成 Proxy，一是懒劫持，初始化时不递归所有属性，大对象加载更快；二是依赖收集更精准，修改数据只触发用到该数据的组件更新，避免无效渲染

3. fragment
	- Vue2 限制：组件必须有唯一根节点（如 `<div>` 包裹），哪怕只是为了满足语法要求，也要多一层无用的 DOM 节点；
	- Vue3 优化：支持多根节点，无需额外包裹标签，减少 DOM 层级和节点数量：
4. teleport
5. suspense


# 体积&构建
**Vue 2**
	因为全局 API 无法Tree-shaking，打包体积大

**Vue 3**
	采用模块化设计，所有 API 按需导入，Tree-shaking 更彻底，打包体积更小，而且适配 Vite 等工具，构建速度也更快

