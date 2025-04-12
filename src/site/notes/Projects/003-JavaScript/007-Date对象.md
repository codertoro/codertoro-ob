---
{"type":"javascript","title":"007-Date对象","tags":["projects/javascript"],"author":"codertoro","establish":"2025-04-12","update":"2025-04-12","dg-publish":true,"permalink":"/Projects/003-JavaScript/007-Date对象/","dgPassFrontmatter":true,"created":"2025-04-12T10:56:25.258+08:00","updated":"2025-04-12T11:19:47.803+08:00"}
---

- date 是js中的内置对象，用来处理和操作日期和时间
- Date对象包含了日期和时间的相关方法，能够对日期进行计算、比较、格式化
- 创建Date对象：
	- 通过无参构造函数创建当前的日期和时间
		- `let time = new Date();`
	- 通过字符串创建指定的日期和时间
<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">

<div class="markdown-embed-title">

# INDEX

</div>


```js
let dateFromString = new Date("2023-12-25 10:30:00");
console.log(dateFromString);  
// 输出：Mon Dec 25 2023 10:30:00 GMT+0800 (中国标准时间)

```

</div></div>

	- 通过有参构造函数创建（指定的日期）
<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">

<div class="markdown-embed-title">

# INDEX

</div>


```js
let customDate = new Date(2022, 11, 31, 23, 59, 59);  
console.log(customDate);  
// 输出：Sat Dec 31 2022 23:59:59 GMT+0800 (中国标准时间)

```

</div></div>

	- 通过时间戳创建日期
		- 获取当前时间戳
<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">

<div class="markdown-embed-title">

# INDEX

</div>


```js
let timestamp_ms = Date.now(); // 毫秒级
let timestamp_ms2 = new Date().getTime();//毫秒级（第二种写法）
let timestamp_s = Math.floor(Date.now() / 1000); // 秒级

console.log("毫秒级时间戳:", timestamp_ms);  
console.log("秒级时间戳:", timestamp_s);

```

</div></div>

		- 用时间戳创建日期对象
<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">

<div class="markdown-embed-title">

# INDEX

</div>


```js
let fromTimestamp = new Date(1672531199000);  // 这个是 2022-12-31 23:59:59 的毫秒数
console.log(fromTimestamp);  
// 输出：Sat Dec 31 2022 23:59:59 GMT+0800 (中国标准时间)

```

</div></div>

			- 时间戳：值某个特定时间点以来的时间长度，通常以秒或毫秒为单位(Unix纪元时间)
			  Unix：指的是从1970年1月1日 00:00 开始所经过的毫秒数
			- 