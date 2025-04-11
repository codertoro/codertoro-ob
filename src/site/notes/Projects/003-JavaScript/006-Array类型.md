---
{"type":"javascript","title":"006-Array类型","tags":["projects/javascript"],"author":"codertoro","establish":"2025-04-11","update":"2025-04-11","dg-publish":true,"permalink":"/Projects/003-JavaScript/006-Array类型/","dgPassFrontmatter":true,"created":"2025-04-11T10:52:20.702+08:00","updated":"2025-04-11T14:38:34.723+08:00"}
---

# 1. 数组基础
- 创建
```js
let arr1  = new Array(e1,e2,e3);
let arr2 = [e1,e2,e3];
let arr3 = [];  //创建空数组
```
- 读取 
	- 下标读取 `arr[i]`
- 赋值
	- `arr[9] = "新增值"`
- 长度
	- `arr.length`
- **注意：** 
	- 同一个数组其实可以存储**不同**数据类型的元素
	- **如果同时存储了不同的数据类型元素，不同的遍历方式会有很大差异，包括：**
		- `for  of`
		- `for in`
		- `forEach`
# 2. 数组的方法
- 增
	- `push()` 尾加多
	- `unshift()` 头加多
- 删
	- `pop()` 尾删一
	- `shift()` 尾加多
- 改
	- `splice(n1,n2,add1,add2...)` 任意位置  增 删 多  
		- n1下标，n2 删除个数 add 插入内容
		- 改变原数组
		- 返回值：新数组，包含被删除项
	- `slice(a,b)`  截取子数组  
		- 支持负数，表示倒数几项
```js
let arr = ['A','B','C','D','E','F'];
let arr1 = arr.slice(2,5);
let arr2 = arr.slice(2);
let arr3 = arr.slice(2,-1);
console.log(arr1);
console.log(arr2);
console.log(arr3);
```
![|269](https://img.codertoro.top/Bucket/Projects/003-JavaScript/20250411134744189.png)
- 改
	- `join(间隔字符)`  数组转字符串
		- **不改变原数组**
		- 返回值：String
		- 与`split()` 搭配使用
```js
let arr = ['A','B','C','D','E','F'];
let arr1 = arr.join();
let arr2 = arr.join(""); //空字符串
let arr3 = arr.join("#");
let arr4 = arr.join(" "); //三个空格
console.log(arr1);
console.log(arr2);
console.log(arr3);
console.log(arr4);
console.log(arr); //判断是否改变原数组
```
- 运行结果：
![|360](https://img.codertoro.top/Bucket/Projects/003-JavaScript/20250411135635485.png)

- 改
	- `concat(arr1,arr2,arr3,...)` 拼接数组
		- **不改变原数组**
		- 返回值：拼接后的Array
```js
let arrA = ['A','B','C'];
let arrB = ['D','E','F'];
let arr1 = arrA.concat(arrB);
console.log(arr1);
console.log(arrA);
console.log(arrB);
```

![|318](https://img.codertoro.top/Bucket/Projects/003-JavaScript/20250411140222996.png)

- 改
	- `reverse()` 倒置数组
		- 改变原数组
		- 返回值：倒置后的数组（和倒置后的原数组是**同一个数组，指向同一块数组内存**）
```js
let arrA = ['A','B','C'];
let arr1 = arrA.reverse();
console.log(arr1);
console.log(arrA);
//测试倒置后arrA和arr1是不是同一个数组
arr1[3] = "D";
console.log(arr1);
console.log(arrA);
```

![|295](https://img.codertoro.top/Bucket/Projects/003-JavaScript/20250411141355789.png)

- 查
	- `includes()` 
		- 语法：`arr.includes(valueToFind[,fromIndex])` 
		- 不改变原数组
		- 返回值：`Boolean` 即true/false
		- **比较方式：** 严格比较 ===   (引用类型比较要注意)
		- `valueToFind` : 要查找的值
		- `fromIndex` : 从这个索引开始查找，默认0 ，支持负数（表示从尾部开始查找）
		- 