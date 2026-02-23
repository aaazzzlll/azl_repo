func.call(thisArg, arg1, arg2, ... ,argN)
`thisArg`:在调用`func`时要使用的`this`值
`arg1, ... ,argN`：函数的参数

如果省略`thisArg`参数，则默认为`undefined`。在非严格模式下，`this`值将被替换为`globalThis`(类似于全局对象)
在严格模式下，`this` 的值不会被替换，因此它保持为 `undefined`。