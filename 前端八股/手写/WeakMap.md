WeakMap的键必须是对象，不能是原始值
WeakMap不支持迭代以及`keys(),values(),entries()`方法，所以没有办法获取WeakMap的所有键或值
WeakMap只有以下方法：
- `weakMap.get(key)`
- `weakMap.set(key, value)`
- `weakMap.delete(key)`
- `weakMap.has(key)`


```javascript
let a = { self: null };
a.self = a;  // 循环引用

let copy = deepClone(a);   // 拷贝成功，不会栈溢出

// 假设业务结束
a = null;                  // 原对象 a 应该被回收

// 如果用的是 Map → a 仍然被 cache 强引用 → 无法回收 → 内存泄漏
// 如果用的是 WeakMap → cache 对 a 是弱引用 → a 可被正常 GC
```

**为什么在深拷贝中必须使用WeakMap：**
用 Map 会让“已经拷贝完的原对象”被 Map 强引用住，即使你把原对象设为 null 或它已经脱离业务作用域，它仍然不会被垃圾回收，导致内存泄漏。 
WeakMap 是弱引用，当原对象在业务代码中没有任何强引用时，WeakMap 里的这条记录会自动被垃圾回收器清理，不会阻止原对象的释放。