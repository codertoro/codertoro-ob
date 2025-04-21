---
{"type":"java","title":"250419-hashCode()和equals()关系","tags":["exercises/java"],"author":"codertoro","establish":"2025-04-19","update":"2025-04-19","dg-publish":true,"java":true,"permalink":"/Exercises/Java/250419-hashCode()和equals()关系/","dgPassFrontmatter":true,"created":"2025-04-19T15:03:30.930+08:00","updated":"2025-04-19T15:14:42.171+08:00"}
---

![](https://img.codertoro.top/Bucket/Exercises/Java/20250419150348935.png)

```java

```
```

```
> [!success]- 答案


> [!success]- 题源
![](https://img.codertoro.top/Bucket/Exercises/Java/20250419150409159.png)


> [!failure]- 错因
hashMap底层是一个数组，数组每一位为一个桶，也是链表的头部/红黑树根节点。如果要将a对象存入hashMap,先通过hashCode(a)计算出哈希值，比如123456，然后哈希值%数组长度，得到数组下标，比如8，数组每一位就是一个链表的头部，或者是一个红黑树的根节点，如果该下标为8的数组指向null，说明该第8个桶为空，直接存入a，如果不指向null，则判断是链表还是红黑树，链表的话，需要挨个用equals比较key是否相同,**时间复杂度为O(n)**，有相同的，则替换value，没有则新增一组key-value。如果是红黑树结构，查找相率会快很多，**时间复杂度为O(logn)**,具体实现细节目前还不会，大概的原理就是类似于二分查找，每次equals会返回一个确定的查找方向

