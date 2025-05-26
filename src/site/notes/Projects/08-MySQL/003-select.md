---
{"type":"mysql","title":"003-select","tags":null,"author":"codertoro","establish":"2025-05-19","update":"2025/05/22 16:30","dg-publish":true,"permalink":"/Projects/08-MySQL/003-select/","dgPassFrontmatter":true,"created":"2025-05-19T17:43:20.245+08:00","updated":"2025-05-22T17:04:12.348+08:00"}
---

# 1. **1. 基本语法**
```sql
select 列1,列2,... from 表名 where 条件;
```

说明：
- 列1，列2，指的是要查询的列，`*`用于表示查询所有列
- 表名：要查询的表
- where: 用来过滤结果的条件

# 2. 常见的比较运算符
1. 等于号 `=`
2. 不等于号 `!=` 或者 `<>`
3. 大于 `>`
4. 小于 `<`
5. 大于等于 `>=`
6. 小于等于 `<=`
7. `between ... and ...` 检查某个字段是否在指定范围内（包括边界）
8. `IN`  `select * from 表名 where id in (10,20,30,50);`
9. `NOT IN` 
10. `like` 
	- 通常与通配符一块使用：`(%,_)` 
	- `%` 匹配0或多个字符
	- `_` 匹配一个字符
	- 示例：`select * from 表名 where 列名 like '%张%'` 
	- 查找某列中包含`张` 的所有行
11. `is null`
12. `is not null`

# 3. 常用的复合条件
1. `and`连接多个条件，所有条件都为true时，结果才为true
2. `or`
3. `not`如果`not`后面为true，`not`会使其变为false
4. `()`组合条件，确保优先级
5. `xor`异或运算，**相同返回false,不同返回true**

# 4. 函数
## 4.1. 聚合函数
1. `count()` 用来统计记录数量的 , **忽略null**
    - `select COUNT(id) FROM user;`
2. `sum()` 对某一列的值进行求和
	- `SELECT sum(score) FROM user2;`
3. `avg()` 求某一列的平均数
	- `SELECT avg(score) FROM user2;`
4. `max()` 求最大值
	- `SELECT max(score) FROM user2;`
5. `min()` 求最小值
	- `SELECT min(score) FROM user2;`
- `group by` 分组：
	- `select 列名1,聚合函数(列名) from 表名 where 条件 group by 列名1,列名2;`
- `having` 过滤分组数据
```sql
select 列名1,聚合函数(列名) from 表名 
where 条件 
group by 列名1,列名2 
having 条件;
```

- `order by` 对查询结果进行排序
	- 注意：`null` 被认为是最小值
```sql
select 列名1,列名2,聚合函数(列名) from 表名
where 条件
order by 列名1[asc/desc],列名2[asc/desc];
```

- `limit` 分页
```sql
select 列名1,列名2 from 表名
where 条件
limit n1,n2; -- n1表示查询结果的索引值，从0开始，n2表示每页显示多少条查询结果
-- 实际开发中n1 =（当前页数-1）* n2
```

- `distinct` 去除重复行
```sql
SELECT DISTINCT username FROM user2;
```

## 4.2. 时间函数
- `now()`
- `curdate()`
- `curtime()`
- `sysdate()`
- `utc_timestamp()`
- `date_format(data,format)`
	- `data` : 日期/日期函数
	- `format` ： 格式： `(%Y-%M-%D %h:%i:%s)`
	- **修改后：**`SELECT DATE_FORMAT(now(), '%Y-%m-%d %H:%i:%s');`
- `time_to_sec(time)` 
	- `time` : 格式为`HH:MM:SS` 格式的时间字符串或时间字段
	- 返回值：从`00:00:00` 开始的总秒数
- `datediff(date1,date2)` 计算两个日期相差的天数
- `extract()` 用于从日期或时间中提取特定的部分
	- `extract(unit from date)` 
		- `unit` : 提取的部分  
			- 取值：`year month day hour minute second week quarter microsecond year_month day_hour`
		- `date` : 
			- 日期字符串 如`2023-12-31`
			- 日期字段名
			- 日期函数，如:`now()` `curdate()` 
- `unix_timestamp()` 用于处理时间戳的操作
	- 从 1970 年1月1日00:00:00 开始，距今的**秒数**

## 4.3. 字符串的函数
- `concat(str1,str2)`  字符串拼接
	- **注意：任意一个字符串为null,结果为null**
- `concat_ws(sep,s1,s2..)` :  `concat()` 的加强版
	- `sep` : 可以指定字符串之间连接的字符
	- **会忽略null**
- `char_length(str)` 返回字符数
- `length(str)` 返回字节数
- `format(X,D)` 
	- `X` : 要格式化的数字
	- `D` : 保留小数位数
- `left(str,len)` 和 `right(str,len)` 
	- `left(str,len)` : 从左边开始截取`len`个字符
		- `str` : 原始字符串
		- `len` : 截取的长度
	- `right(str,len)` : 从右边开始截取`len` 个字符串
- `substring(str,pos[,len])` 字符串的截取
	- `str` : 要截取的字符串
	- `pos` : 起始位置 **（从1开始）**
	- `len` : 可选项： 截取的长度 **（单位是字符）**
	- 注意： 
		- `len` :如果不写，从 `pos` 其实位置开始，到最后结束
		- `pos` 从 1 开始计数，**如果是负数，表示从字符串末尾开始**
- `substring_index(str,delim,count)` 
	- 截取字符串的函数，专门用来按照分隔符来截取字符串
	- `str` ： 原始字符串
	- `delim` ： 分隔符，如（`/` 、`,`）
	- `count` ： 截取的方向和次数
		- 正数： 从左往右第几个分隔符，保留左边部分
		- 负数：从右往左第几个分隔符，保留右边部分
- `locate(substr,str)`  
	- 用于查找子字符串在字符串中的位置，返回字符串在目标字符串中的起始位置，如果找不到，返回 0。
	- `substr` ： 要查找的字符串
	- `str` ： 要搜索的目标字符串
	- **返回值：** 返回子字符串在目标字符串中首次出现的位置（**从 1 开始计数**），找不到返回 0
- `trim([remstr from] str)` 
	- 用来去除字符串两端的空格或指定字符
	- `str` 要处理的字符串
	- `remstr` ： 要去除的字符集（默认是空格）
## 4.4. 数学函数
- `round(x,d)`
	- 用于四舍五入的函数，可以控制保留的小数位数
	- `x` : 要四舍五入的数字
	- `d` : 保留的小数位数（默认为 0，表示四舍五入为整数）
	- **注意：**
		- 如果 `d` 为正数，则是保留 `d` 位小数
		- 如果 `d` 为 0，则四舍五入为整数
		- 如果为负整数，则会将数字四舍五入到最接近的 10 的倍数（或者更大单位）
- `rand()`
	- 生成随机浮动数的函数，返回一个在 0-1 之间的随机浮动数（小数）
	- **注意：**
		- 没有参数，如果括号里写一个固定值，得到的随机数将也是一个固定值
		- **范围：** `[0,1）` 包括 0，不包括 1
- `MD5(str)`
	- 用于生成字符串的 MD 5 哈希值函数
	- `str` ： 要进行 MD 5 哈希计算的字符串
	- 功能： 返回输入字符串的 MD 5 哈希值，结果是一个 32 位的 16 进制的字符串（即 128 位） **结果不可逆**， **但是不安全，因为可以建立密码库**
- `row_count()` 
	- 返回上一个 sql 语句影响的行数

# 5. 多表联查
## 5.1. 内连接
- `inner join ... on` 常用的连接语句，用于将两个或多个表根据关联条件连接起来，值返回满足条件的记录
- 基本语法
```sql
select 列1，列2,...
from 表A
inner join 表B
on 表A.关联列 = 表B.关联列 
```

## 5.2. 外连接
- `left join .. on ..`  `right join .. on ..` 
- **核心：即使一边表中没有匹配的数据，也会显示另边表的所有数据，为匹配的部分以 null 补上**
### 5.2.1. 左连接
- 基本语法：
```sql
select 列1，列2,...
from 表A
left join 表B
on 表A.关联列 = 表B.关联列 
```
- 返回的数据：表 A 中的所有数据+ 表 B 中匹配的数据（不匹配的以 null 补充）
### 5.2.2. 右连接
- 基本语法
```sql
select 列1，列2,...
from 表A
right join 表B
on 表A.关联列 = 表B.关联列 
```
- 返回的数据：表 B 中的所有数据+ 表 A 中匹配的数据（不匹配的以 null 补充）

# 6. 子查询
- 子查询是一个嵌套在其他 SQL 语句中的 `select` 语句。通常为主查询提供数据
- 常见的子查询分类：
	1. **标量子查询** ： 子查询只返回一个值（一个单元格）
	2. **列子查询：** 子查询返回一列，多行
	3. **行子查询：** 子查询返回一整行，用于和多列比较
	4. **表子查询：** 子查询饭一整张表，通常在 `from` 子句中
		- **注意：表子查询必须有别名**