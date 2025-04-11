---
{"type":"javascript","title":"call()方法详解","tags":null,"author":"codertoro","establish":"2025-04-10","update":"2025-04-10","dg-publish":true,"permalink":"/Projects/003-JavaScript/call()方法详解/","dgPassFrontmatter":true,"created":"2025-04-10T15:22:05.548+08:00","updated":"2025-04-10T22:35:39.203+08:00"}
---

- 基本语法
- `func.call(thisArg, arg1, arg2, ...);`
- 典型例子：
```js
function Animal(name) {
  this.name = name;
}

function Dog(name) {
  Animal.call(this, name);  // 将 `this` 绑定到 `Dog` 实例上
}

const dog1 = new Dog('Buddy');
console.log(dog.name);  // 输出: Buddy

```
- 这个例子中，
- `Dog()` 构造函数中的 `this` 指向构造出来的实例对象`dog1` ,
- `call()` 会将其第一个参数传递给调用他的函数(这里指`Animal()` 构造函数)**内部的**`this` ,
- 然后将`call()` 的其余参数(比如这里的`name`) 作为实际参数传递给`Animal` 的形参`name`，
- `call()` 函数执行完毕之后，执行`Animal()` 构造函数，
- **此时** `Animal()` 函数内部的`this` 指向的是`dog1` 而不是Animal的实例对象。
- **因此：在dog1被实例化出来时，会带有Animal()构造函数中的全部属性**

- **Animal()的其他属性（没写在构造函数中的），是没有继承的**

