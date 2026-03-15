---
Date: 2026-03-15
upstream: "[[Vue 2和Vue 3的核心区别]]"
related: 相关卡1
tags:
---
#### 劫持粒度
- `Object.defineProperty`只能逐个劫持属性，如果要监听一个对象的多个属性，需要遍历对象+逐个定义，且无法监听未提前定义的属性
- `Proxy`劫持整个对象，可以监听对象的所有属性，无需逐个定义

#### 支持的拦截操作
- `Object.defineProperty` 仅支持 `get`/`set` 两种操作；
- `Proxy` 支持 13 种拦截操作，覆盖对象的绝大部分行为。属性新增/删除，数组下标修改(`arr [0]=1`)，数组方法(push/pop)均支持

#### 设计理念
- `Object.defineProperty`：直接修改原对象的属性描述符，**污染原对象**；
- `Proxy`：创建一个新的代理对象，所有操作通过代理对象完成，**原对象保持纯净**

#### 兼容性
- `Object.defineProperty`：兼容性更好，兼容 ES5 环境，支持 IE9+
- `Proxy`：ES6 特性，不支持 IE，需要转译（但转译后无法实现完整功能）