# javascript_interview-question

javascript interview questions

## 1. new 的实现原理是什么？

1. 创建一个空对象，构造函数中的 this 指向这个空对象
2. 这个新对象被执行 [[原型]] 连接
3. 执行构造函数方法，属性和方法被添加到 this 引用的对象中
4. 如果构造函数中没有返回其它对象，那么返回 this，即创建的这个的新对象，否则，返回构造函数中返回的对象。

```
function _new() {
    const target = {};

    const [constructor, ...args] = [...arguments];

    target.__proto__ = constructor.prototype;

    let result = constructor.apply(target, args);

    if (result && ((typeof result === 'object') || typeof result === 'function')) {
        return result;
    }

    return target;
}
```
