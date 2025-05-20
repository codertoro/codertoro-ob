---
{"type":"mysql","title":"003-select","tags":null,"author":"codertoro","establish":"2025-05-19","update":"2025/05/19 17:43","dg-publish":true,"permalink":"/Projects/08-MySQL/003-select/","dgPassFrontmatter":true,"created":"2025-05-19T17:43:20.245+08:00","updated":"2025-05-19T17:55:21.287+08:00"}
---

# 1. 基本语法
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