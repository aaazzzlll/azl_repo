this的指向取决于函数的调用方式
1. 默认绑定
独立函数调用，this指向全局对象（浏览器中为window），严格模式下为undefined
2. 隐式绑定
作为对象方法调用，this指向调用对象
3. 显式绑定
通过call、apply、bind指定this
4. new绑定
构造函数调用，this指向新创建的对象
5. 箭头函数
没有自己的this，继承外层作用域的this