- *配置 ESLint + Prettier 统一代码规范，并利用 OpenAPI 工具根据后端 Swagger 文档自动生成 TypeScript 模型与 API 请求代码。*

1.ESLint：检查代码质量
	检查Vue规则：检查.vue文件语法
	检查TS语法：如未使用的变量、类型错误
	关闭所有和格式相关的规则，交给prettier处理，避免冲突
2. Prettier：统一代码格式
	在项目中Prettier我使用的是默认规则，保存时自动格式化
3. OpenAPI：自动生成API请求代码和TypeScript类型，将后端接口文档变成可以直接调用的函数
	



