---
{"type":"javascript","title":"003-String","tags":["projects/javascript"],"author":"codertoro","establish":"2025-04-05","update":"2025-04-05","dg-publish":true,"categories":["数据类型","基本数据类型"],"permalink":"/Projects/003-JavaScript/003-String/","dgPassFrontmatter":true,"created":"2025-04-05T20:30:43.506+08:00","updated":"2025-04-12T17:13:52.237+08:00"}
---

# 1. 对象分类
- 内置对象
	- `String`  
	- `Array`
	- `Date`
	- `Math`
- 自定义对象
# 2. `String` 对象的常用方法
- `length` **属性** 获取长度
- `toLowerCase()` 大写转小写
- `toUpperCase()` 小写转大写
- `charAt(n)` 获取第n+1个字符，n是下标，第一个字符下标是0
- `substring(start,end)`  截取字符串的某一部分，截取范围[start , end)
- `slice(start,end)` 同上，但是可以接受负数，表示从字符串的末尾开始，最后一位的索引为-1
- `str.replace(原字符串片段，替换字符串)` 
- `str.replace(正则表达式，替换字符串)` 
```js
//字符串
var str = "I love javascript!";
var str_new = str.replace("javascript", "lvye");
document.write(str_new);
//正则
var str = "I am loser, you are loser, all are loser.";
var str_new = str.replace(/loser/g, "hero");
//区别对比
var str_new = str.replace(/loser/g, "hero"); //会替换所有loser
var str_new = str.replace("lose", "hero"); //只会替换第一的loser
```
- `split("分隔符",n)` n代表获取分割后前n个元素
- `str.indexOf(指定字符串)`  返回首次出现的下标，找不到返回-1
- `str.lastIndexOf(指定字符串)`  返回最后出现的下标，找不到返回-1
	- 扩展：`match()` `search()` 功能类似
- `trim()` 去除字符串两端的空格,可以去除多个空格
```js
const str = "     Hello Lvye ";
let new_str = str.trim();
console.log(new_str);
```
- `includes(Value)` 判断字符串是否有指定字符串，结果返回true/false
- `str.repeat(n)` 返回一个新字符串，重复str字符串n次
