---
{"type":"javascript","title":"010-Date日期","tags":["projects/javascript"],"author":"codertoro","establish":"2025-04-12","update":"2025-04-12","dg-publish":true,"categories":["数据类型","引用数据类型"],"permalink":"/Projects/003-JavaScript/010-Date日期/","dgPassFrontmatter":true,"created":"2025-04-12T10:56:25.258+08:00","updated":"2025-04-12T17:24:16.525+08:00"}
---

- date 是js中的内置对象，用来处理和操作日期和时间
- Date对象包含了日期和时间的相关方法，能够对日期进行计算、比较、格式化
# 1. 创建Date对象：
- 通过无参构造函数创建当前的日期和时间
	- `let time = new Date();`
- 通过字符串创建指定的日期和时间
<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">

<div class="markdown-embed-title">

# CODE-字符串创建日期

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

# CODE-有参构造创建

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

# CODE-获取当前时间戳

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

# CODE-用时间戳创建日期

</div>


```js
let fromTimestamp = new Date(1672531199000);  // 这个是 2022-12-31 23:59:59 的毫秒数
console.log(fromTimestamp);  
// 输出：Sat Dec 31 2022 23:59:59 GMT+0800 (中国标准时间)

```

</div></div>

		- 时间戳：值某个特定时间点以来的时间长度，通常以秒或毫秒为单位(Unix纪元时间)
		  Unix：指的是从1970年1月1日 00:00 开始所经过的毫秒数
# 2. 常用方法
## 2.1. 获取日期和时间
- `getFullYear()`  年
- `getMonth()`  月（0-11）
- `getDate()` 日期（1-31）
- `getHours()` 小时（0-23）
- `getMinutes()` 分钟（0-59）
- `getSeconds()` 秒 （0-59）
- `getMiliseconds()` 毫秒 （0-999）
- `getDay()` 星期（0-6）
## 2.2. 设置日期和时间
- `setFullYear(year)` 年
- `setMonth(month)` 月（0-11）
- `setDate(date)` 日期（1-31）
- `setHours(hours)` 小时（0-23）
- `setMinutes(minutes)` 分钟（0-59）
- `setSeconds(seconds)` 秒（0-59）
- `setMilliseconds(milliseconds)` 毫秒（0-999）
## 2.3. 日期转字符串
- `toString()`           Wed Dec 25 2030 12:30:45 GMT+0800 (中国标准时间)
- `toDateString()`  Wed Dec 25 2030
- `toTimeString()`  12:30:45 GMT+0800 (中国标准时间)
- `toLocalString()` 2030/12/25 12:30:45

## 2.4. 测试代码

<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">

<div class="markdown-embed-title">

# CODE-测试代码

</div>


```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Date 对象方法测试</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      padding: 20px;
    }
    button {
      padding: 10px 15px;
      margin-bottom: 20px;
    }
    pre {
      background: #f4f4f4;
      padding: 10px;
      border-radius: 6px;
    }
  </style>
</head>
<body>
  <h2>Date 对象常用方法测试</h2>
  <button onclick="testDate()">测试 Date 方法</button>
  <pre id="output">点击按钮查看结果...</pre>
  <script>
    function testDate() {
      let output = "";
      // 当前时间
      const now = new Date();
      output += "▶ 当前时间对象: " + now + "\n\n";
      // 1. 获取时间的方法
      output += "【获取时间】\n";
      output += "年份: " + now.getFullYear() + "\n";
      output += "月份 (0-11): " + now.getMonth() + "\n";
      output += "日期 (1-31): " + now.getDate() + "\n";
      output += "小时: " + now.getHours() + "\n";
      output += "分钟: " + now.getMinutes() + "\n";
      output += "秒: " + now.getSeconds() + "\n";
      output += "毫秒: " + now.getMilliseconds() + "\n";
      output += "星期几 (0-6): " + now.getDay() + "\n\n";
      // 2. 设置时间的方法
      const future = new Date();
      future.setFullYear(2030);
      future.setMonth(11); // 12月
      future.setDate(25);
      future.setHours(12);
      future.setMinutes(30);
      future.setSeconds(45);
      future.setMilliseconds(123);
      output += "【设置后的时间】\n";
      output += "设置为: " + future + "\n\n";
      // 3. 转换为字符串
      output += "【字符串表示】\n";
      output += "toString(): " + future.toString() + "\n";
      output += "toDateString(): " + future.toDateString() + "\n";
      output += "toTimeString(): " + future.toTimeString() + "\n";
      output += "toLocaleString(): " + future.toLocaleString() + "\n";
      document.getElementById("output").textContent = output;
    }
  </script>
</body>
</html>
```

</div></div>

- 运行结果
![|538](https://img.codertoro.top/Bucket/Projects/003-JavaScript/20250412160541460.png)

