---
{"type":"javascript","title":"002-Number","tags":["projects/javascript"],"author":"codertoro","establish":"2025-04-11","update":"2025-04-11","dg-publish":true,"categories":["数据类型","基本数据类型"],"permalink":"/Projects/003-JavaScript/002-Number/","dgPassFrontmatter":true,"created":"2025-04-11T09:45:48.695+08:00","updated":"2025-04-12T17:13:59.278+08:00"}
---

# 1. Number()函数
- 基本用途
	- 将其他类型转化为数字类型
- 转化规则

| 其他类型          | 转化为数字类型的结果                      |
| ------------- | ------------------------------- |
| 字符串           | 如果是纯数字字符串，返回<br>不是纯数字，返回**NaN** |
| 布尔值           | true   1<br>false  0            |
| null          | 0                               |
| undefined     | NaN                             |
| ""   空字符串     | 0                               |
| " "  只用空格的字符串 | 0                               |
| 数字字符串（含字符）    | parseInt( )  parsefloat()       |

