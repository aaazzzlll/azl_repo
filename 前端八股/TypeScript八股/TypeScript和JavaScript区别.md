---
Date: 2026-03-11
upstream: " 父卡片"
related: 相关卡1
tags:
---
1. 类型系统
	JavaScript是动态弱类型语言：变量类型在运行时才确定，存在隐式转换类型
	TypeScript是静态强类型语言：编写代码时就指定变量类型，不存在隐式转换类型

2. 错误发现时机
	JavaScript：只有代码跑起来才会发现错误
	TypeScript：写代码时或编译时就发现错误

3. 代码提示/补全
	JavaScript：编辑器只能猜变量类型，提示少且不准确
	TypeScript：编辑器可以精准知道变量类型，自动提示属性/方法

4. 学习成本
	TypeScript兼容所有JS语法，还增加了类型相关语法
	- 类型注解：`let a: number = 1`、`function fn(a: string): boolean`；
	- 类型别名：`type User = { name: string; age: number }`；
	- 接口：`interface Person { id: number }`；
	- 泛型：`function fn<T>(data: T): T`（处理通用类型）；
	- 枚举：`enum Status { Success = 0, Error = 1 }`；
	- 可选链 / 空值合并（TS 也支持，和 ES6+ 一致）。
5. 运行环境
	JavaScript：写好直接运行在浏览器/Node.js
	TypeScript：必须先通过tsc（TS编译器）编译成JS，才能运行

6. 适用场景
	JavaScript适合小型项目，快速原型开发
	TypeScript适合中大型项目，团队协作，框架开发