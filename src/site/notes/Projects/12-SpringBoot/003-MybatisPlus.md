---
{"type":"springboot","title":"003-MybatisPlus","tags":null,"author":"codertoro","establish":"2025-07-02","update":"2025/07/02 21:05","dg-publish":true,"permalink":"/Projects/12-SpringBoot/003-MybatisPlus/","dgPassFrontmatter":true,"created":"2025-07-02T21:05:25.636+08:00","updated":"2025-07-02T23:16:20.224+08:00"}
---

# **MyBatis-Plus 完整笔记**

  

## **一、常用方式总结**

  

### **1.** 

### **BaseMapper<T>**

###  **自带方法**

  

将 Mapper 接口继承 BaseMapper<T>，自动拥有基础 CRUD 功能

|**方法名**|**作用**|
|---|---|
|selectById(id)|根据 ID 查询|
|selectList(wrapper)|条件查询列表|
|selectOne(wrapper)|查询单个结果|
|selectCount(wrapper)|条件总数量|
|insert(entity)|插入新记录|
|updateById(entity)|根据 ID 更新|
|deleteById(id)|根据 ID 删除|

### **2.** 

### **ServiceImpl**

###  **通用方法**

  

使用 ServiceImpl<M extends BaseMapper<T>, T>，实现类中有通用方法

|**方法名**|**等价 Mapper 方法**|
|---|---|
|getById(id)|selectById(id)|
|list()|selectList(null)|
|save(entity)|insert(entity)|
|updateById(entity)|updateById(entity)|
|removeById(id)|deleteById(id)|
|saveOrUpdate(entity)|ID 判断 insert/update|

### **3. Wrapper 条件构造器**

- QueryWrapper<T> / LambdaQueryWrapper<T>
    
- 链式写法，实现动态 SQL
    

  

#### **示例：**

```
LambdaQueryWrapper<User> qw = new LambdaQueryWrapper<>();
qw.eq(User::getName, "张三").gt(User::getAge, 18);
userMapper.selectList(qw);
```

### **4. XML 自定义 SQL**

  

处理复杂 SQL （多表 JOIN、分组、子查询等）

```
<select id="selectUserWithOrders" resultType="UserDTO">
  SELECT u.*, o.total FROM user u
  JOIN orders o ON u.id = o.user_id
  WHERE o.status = #{status}
</select>
```

## **二、推荐使用方案**

|**场景**|**推荐方法**|
|---|---|
|基本增删改查|BaseMapper / ServiceImpl|
|动态条件查询|LambdaQueryWrapper|
|动态更新|LambdaUpdateWrapper|
|复杂查询、分组|XML 定制 SQL|

## **三、方法名列表快照**

  

### **查询**

- selectById(id)
    
- selectOne(wrapper)
    
- selectList(wrapper)
    
- selectCount(wrapper)
    

  

### **新增**

- insert(entity)
    
- save(entity)
    

  

### **更新**

- updateById(entity)
    
- update(entity, wrapper)
    
- saveOrUpdate(entity)
    

  

### **删除**

- deleteById(id)
    
- delete(wrapper)
    
- removeById(id)
    
- remove(wrapper)
    

  

## **四、简单示例**

```
// 条件查询
LambdaQueryWrapper<AddressDO> qw = new LambdaQueryWrapper<>();
qw.eq(AddressDO::getUserId, userId).eq(AddressDO::getIsDefault, 1);
AddressDO addr = addressMapper.selectOne(qw);

// 条件更新
LambdaUpdateWrapper<AddressDO> uw = new LambdaUpdateWrapper<>();
uw.eq(AddressDO::getUserId, userId).set(AddressDO::getIsDefault, 0);
update(uw);
```

## **五、总结**

|**方法类型**|**特点**|**适用场景**|
|---|---|---|
|BaseMapper|基础方法，直接使用|CRUD 基础操作|
|ServiceImpl|层级比 Mapper 高一级，分离逻辑|Controller 调用|
|Wrapper|链式、动态、安全|条件类 SQL|
|XML|SQL 自描写，类 SQL 控制|复杂查询|

---

如有需要，可以继续扩展自定义分页、完善接口统一返回结构等细节。