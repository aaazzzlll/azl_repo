func.call(thisArg, arg1, arg2, ... ,argN)
`thisArg`:在调用`func`时要使用的`this`值
`arg1, ... ,argN`：函数的参数

如果省略`thisArg`参数，则默认为`undefined`。在非严格模式下，`this`值将被替换为`globalThis`(类似于全局对象)
在严格模式下，`this` 的值不会被替换，因此它保持为 `undefined`。

当使用call/apply/bind绑定this时，传入的第一个参数（thisArg）不管是什么类型，最终都会被当做“对象”来对待，如果它本来就不是对象，JavaScript会自动将它包装成对应的对象类型
所以在手写call的时候也要满足call的规范要求，需要对原始值进行包装(Object(thisArg))

==call/apply与bind的区别：==
除了 bind 不立即执行之外，bind 返回的新函数会永久绑定 this，后续无论怎么调用（包括 new），this 都固定不变，而 call/apply 只影响单次调用。