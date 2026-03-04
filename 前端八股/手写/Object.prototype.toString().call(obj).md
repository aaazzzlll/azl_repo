```javascript
Object.prototype.toString.call(null);     // "[object Null]"
Object.prototype.toString.call([]);       // "[object Array]"
```
这是一个通用的类型判断方法，适用于判断各种数据类型，Object.prototype.toString.call(obj) 会返回一个类似 \[object type\] 的字符串
