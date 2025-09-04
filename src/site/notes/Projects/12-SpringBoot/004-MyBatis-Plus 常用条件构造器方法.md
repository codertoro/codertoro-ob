---
{"type":"springboot","title":"004-MyBatis-Plus 常用条件构造器方法","tags":null,"author":"codertoro","establish":"2025-07-23","update":"2025/07/23 15:25","dg-publish":true,"permalink":"/Projects/12-SpringBoot/004-MyBatis-Plus 常用条件构造器方法/","dgPassFrontmatter":true,"created":"2025-07-23T15:25:41.000+08:00","updated":"2025-07-23T15:26:11.188+08:00"}
---

当然可以，下面是 **MyBatis-Plus 常用条件构造器方法** 的整理总结，适用于 QueryWrapper 和 LambdaQueryWrapper。

---

## **✅ MyBatis-Plus 常用查询条件方法一览**

|**方法名**|**说明**|**示例（字段名）**|**示例（Lambda）**|
|---|---|---|---|
|eq|等于 =|.eq("name", "Tom")|.eq(User::getName, "Tom")|
|ne|不等于 !=|.ne("status", 1)|.ne(User::getStatus, 1)|
|gt|大于 >|.gt("age", 18)|.gt(User::getAge, 18)|
|ge|大于等于 >=|.ge("age", 18)|.ge(User::getAge, 18)|
|lt|小于 <|.lt("score", 100)|.lt(User::getScore, 100)|
|le|小于等于 <=|.le("score", 100)|.le(User::getScore, 100)|
|between|区间 BETWEEN AND|.between("age", 18, 30)|.between(User::getAge, 18, 30)|
|notBetween|不在区间|.notBetween("age", 18, 30)|.notBetween(User::getAge, 18, 30)|
|like|模糊匹配 %xx%|.like("name", "Tom")|.like(User::getName, "Tom")|
|notLike|不匹配模糊|.notLike("name", "Tom")|.notLike(User::getName, "Tom")|
|likeLeft|左模糊 %xx|.likeLeft("name", "Tom")|.likeLeft(User::getName, "Tom")|
|likeRight|右模糊 xx%|.likeRight("name", "Tom")|.likeRight(User::getName, "Tom")|
|in|包含 IN (...)|.in("id", list)|.in(User::getId, list)|
|notIn|不包含 NOT IN (...)|.notIn("id", list)|.notIn(User::getId, list)|
|isNull|IS NULL|.isNull("deleted_at")|.isNull(User::getDeletedAt)|
|isNotNull|IS NOT NULL|.isNotNull("updated_at")|.isNotNull(User::getUpdatedAt)|
|orderByAsc|升序排序|.orderByAsc("age")|.orderByAsc(User::getAge)|
|orderByDesc|降序排序|.orderByDesc("age")|.orderByDesc(User::getAge)|
|last|拼接 SQL 末尾语句|.last("LIMIT 1")|不适用 Lambda|
|select|指定查询字段|.select("id", "name")|.select(User::getId, User::getName)|
|or / and|手动拼接 AND / OR|.or().eq(...).or().like(...)|同上|

---

### **✅ 组合查询示例**

```
LambdaQueryWrapper<User> wrapper = new LambdaQueryWrapper<>();
wrapper.ge(User::getAge, 18)
       .le(User::getAge, 30)
       .likeRight(User::getUsername, "张")
       .orderByDesc(User::getCreateAt);
```

---

如果你希望我出一张图或写成 Markdown 方便保存，也可以告诉我！