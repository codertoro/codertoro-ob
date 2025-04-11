---
{"type":"javascript","title":"006-Array类型","tags":["projects/javascript"],"author":"codertoro","establish":"2025-04-11","update":"2025-04-11","dg-publish":true,"permalink":"/Projects/003-JavaScript/006-Array类型/","dgPassFrontmatter":true,"created":"2025-04-11T10:52:20.702+08:00","updated":"2025-04-11T18:25:27.942+08:00"}
---

# 1. 数组基础
- 创建 
<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">

<div class="markdown-embed-title">

# INDEX

</div>


```js
let arr1  = new Array(e1,e2,e3);
let arr2 = [e1,e2,e3];
let arr3 = [];  //创建空数组
```

</div></div>

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
<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">

<div class="markdown-embed-title">

# INDEX

</div>


```js
let arr = ['A','B','C','D','E','F'];
let arr1 = arr.slice(2,5);
let arr2 = arr.slice(2);
let arr3 = arr.slice(2,-1);
console.log(arr1);
console.log(arr2);
console.log(arr3);
```

</div></div>
![|269](https://img.codertoro.top/Bucket/Projects/003-JavaScript/20250411134744189.png)
- 改
	- `join(间隔字符)`  数组转字符串
		- **不改变原数组**
		- 返回值：String
		- 与`split()` 搭配使用
<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">

<div class="markdown-embed-title">

# INDEX

</div>


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

</div></div>

		- 运行结果：![|360](https://img.codertoro.top/Bucket/Projects/003-JavaScript/20250411135635485.png)
- 改
	- `concat(arr1,arr2,arr3,...)` 拼接数组
		- **不改变原数组**
		- 返回值：拼接后的Array
<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">

<div class="markdown-embed-title">

# INDEX

</div>


```js
let arrA = ['A','B','C'];
let arrB = ['D','E','F'];
let arr1 = arrA.concat(arrB);
console.log(arr1);
console.log(arrA);
console.log(arrB);
```

</div></div>
![|318](https://img.codertoro.top/Bucket/Projects/003-JavaScript/20250411140222996.png)

- 改
	- `reverse()` 倒置数组
		- 改变原数组
		- 返回值：倒置后的数组（和倒置后的原数组是**同一个数组，指向同一块数组内存**）
<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">

<div class="markdown-embed-title">

# INDEX

</div>


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

</div></div>
![|295](https://img.codertoro.top/Bucket/Projects/003-JavaScript/20250411141355789.png)

- 查
	- `includes()` 
		- 语法：`arr.includes(valueToFind[,fromIndex])` 
		- 不改变原数组
		- 返回值：`Boolean` 即true/false
		- **比较方式：**  **SamevalueZero**  (引用类型比较要注意)
		- `valueToFind` : 要查找的值
		- `fromIndex` : 从这个索引开始查找，默认0 ，支持负数（表示从尾部开始查找）
		- 数据类型判断总结
<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/projects/003-java-script/001/#1bed3c" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">

<div class="markdown-embed-title">

# 数据类型判断

</div>


| 方法             | 严格程度       | 底层原理              | 特殊值备注                            |
| -------------- | ---------- | ----------------- | -------------------------------- |
| Object.is()    | 🌟🌟🌟🌟🌟 | SameValue         | ✅ NaN === NaN，✅ 区分 +0 和 -0       |
| Number.isNaN() | 🌟🌟🌟🌟🌟 | === NaN（无类型转换）    | ✅ 精确判断 NaN，❌ 不误判字符串              |
| includes()     | 🌟🌟🌟🌟🌟 | SameValueZero     | ✅ NaN == =  NaN，✅ +0 === -0（不区分） |
| ===            | 🌟🌟🌟🌟   | Strict Equality   | ❌ NaN !== NaN，✅ +0 === -0（不区分）   |
| indexOf()      | 🌟🌟🌟     | ===               | ❌ 无法识别 NaN，✅ 匹配 +0/-0 (不区分)      |
| isNaN()        | 🌟🌟       | Number() + isNaN  | ⚠️ 易误判：如 isNaN('abc') → true     |
| ==             | 🌟         | Abstract Equality | ❌ NaN，⚠️ 类型自动转换，易出错              |

</div></div>

	- `indexOf()` 
		- 语法：`arr.indexOf(valueToFind[,fromIndex])`
		- 不改变原数组
		- 比较方式：===
			- 示例代码：
<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">

<div class="markdown-embed-title">

# INDEX

</div>


```js
var b = 3;
(function () {
  b = 5;
  var b = 2;
})();
console.log(b);

```

</div></div>

			- 