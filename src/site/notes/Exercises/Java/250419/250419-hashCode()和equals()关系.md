---
{"type":"java","title":"250419-hashCode()和equals()关系","tags":["exercises/java"],"author":"codertoro","establish":"2025-04-19","update":"2025-04-19","dg-publish":true,"java":true,"permalink":"/Exercises/Java/250419/250419-hashCode()和equals()关系/","dgPassFrontmatter":true,"created":"2025-04-19T15:03:30.930+08:00","updated":"2025-05-06T13:46:09.842+08:00"}
---

![](https://img.codertoro.top/Bucket/Exercises/Java/20250419150348935.png)

> [!success]- 答案


> [!success]- 题源
![](https://img.codertoro.top/Bucket/Exercises/Java/20250419150409159.png)


> [!failure]- 错因
hashMap底层是一个数组，数组每一位为一个桶，也是链表的头部/红黑树根节点。如果要将a对象存入hashMap,先通过hashCode(a)计算出哈希值，比如123456，然后哈希值%数组长度，得到数组下标，比如8，数组每一位就是一个链表的头部，或者是一个红黑树的根节点，如果该下标为8的数组指向null，说明该第8个桶为空，直接存入a，如果不指向null，则判断是链表还是红黑树，链表的话，需要挨个用equals比较key是否相同,**时间复杂度为O(n)**，有相同的，则替换value，没有则新增一组key-value。如果是红黑树结构，查找相率会快很多，**时间复杂度为O(logn)**,具体实现细节目前还不会，大概的原理就是类似于二分查找，每次equals会返回一个确定的查找方向
>**Ai改进后：**
>HashMap 底层是一个数组，数组每一格叫做**桶**，每个桶可能是链表的头节点，也可能是红黑树的根节点。
如果要存入对象 a，先用 `hashCode(a)` 计算出初步哈希值，然后经过扰动函数得到更均匀的哈希值。再用 `(哈希值 & (数组长度 - 1))` 定位数组下标。
如果对应桶为空，直接插入。
如果对应桶非空，先判断是链表还是红黑树。
链表：挨个节点用 `equals()` 比较 key，存在则覆盖 value，不存在则插到链表尾部，时间复杂度 O(n)。
红黑树：根据 hash 值、大小关系定位，插入或覆盖，时间复杂度 O(logn)。
当链表长度超过8且数组长度大于64时，链表会转换成红黑树，以提高查找速度。



