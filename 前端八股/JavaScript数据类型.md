基本数据类型（存储在栈中）：
	undefined
	null
	number
	string
	boolean
	symbol（ES6）
	bigint   (ES2020)

引用数据类型（存储在堆中)：
	object（包括数组、函数、日期等）

堆和栈的区别：
	栈：内存分配效率高，自动管理（由编译器分配和释放）
	堆：内存分配灵活，但需要开发者手动管理内存（JS引擎通过垃圾回收机制（GC）自动回收）

精确判断数据类型的方法：[Object.prototype.toString().call(obj)](Object.prototype.toString().call(obj).md)

