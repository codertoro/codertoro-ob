---
{"type":"es6","title":"005-rest参数","tags":null,"author":"codertoro","establish":"2025-04-07","update":"2025-04-07","dg-publish":true,"permalink":"/Projects/004-ES6/005-rest参数/","dgPassFrontmatter":true,"created":"2025-04-07T23:04:22.417+08:00","updated":"2025-04-08T16:42:42.237+08:00"}
---

- ES6 引入rest参数，用于获取函数的实参，用来代替arguments
# 1. ES5 的写法
```javascript
function date(){
	console.log(arguments);
	console.log(typeof(arguments))
}
date('小红','小蓝','小明');
```
- 运行结果如下
![](https://img.codertoro.top//Bucket/Projects/ES6/202504072312140.png)
- 由此可见，`arguments` 的类型是`object`

> [!note]+ arguments的特点
> - 它有什么？
>  索引访问：可以通过 arguments[0], arguments[1] 访问参数；
>  length 属性：可以知道传了多少个参数；
> callee 属性：可以引用当前函数（非严格模式下）；
> 从 ES6 开始，它也具备了 [Symbol.iterator] 方法，因此可以被遍历（比如用 for...of）；
> - 它没有什么？
> 它不是一个真正的 Array，不能直接用 map()、filter() 等数组方法。

# 2. ES6 的写法（rest参数）
- 参数只有rest参数时；
```javascript
function date(...args){
	console.log(args); 
}
date('小红','小蓝','小明');
```
- 运行结果如下：
![](https://img.codertoro.top//Bucket/Projects/ES6/202504072347217.png)
- 还有其他参数时，rest参数必须放到最后
```javascript
function date(a,b,...args){
	console.log(a);
	console.log(b);
	console.log(args)
}
date(1,2,3,4,5,6,7,8);
```
- 结果如下：
![](https://img.codertoro.top//Bucket/Projects/ES6/202504080015580.png)

![](https://img.codertoro.top//Bucket/Projects/ES6/202504080816089.png)

