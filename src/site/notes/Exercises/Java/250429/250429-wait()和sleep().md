---
{"type":"java","title":"250429-wait()和sleep()","tags":["exercises/java"],"author":"codertoro","establish":"2025-04-29","update":"2025-04-29","dg-publish":true,"java":true,"permalink":"/Exercises/Java/250429/250429-wait()和sleep()/","dgPassFrontmatter":true,"created":"2025-04-29T19:37:11.787+08:00","updated":"2025-04-29T19:39:33.340+08:00"}
---

![](https://img.codertoro.top/Bucket/Exercises/Java/20250429193742530.png)

> [!success]- 答案
D

> [!success]- 题源
![](https://img.codertoro.top/Bucket/Exercises/Java/20250429193826452.png)
https://www.nowcoder.com/questionTerminal/943aeab5ab464c5caa7f64ca2638a90a?

> [!failure]- 错因
sleep和wait的区别有： 
1，这两个方法来自不同的类分别是Thread和Object 
2，最主要是sleep方法没有释放锁，而wait方法释放了锁，使得敏感词线程可以使用同步控制块或者方法。 
3，wait，notify和notifyAll只能在同步控制方法或者同步控制块里面使用，而sleep可以在 任何地方使用 synchronized(x){ x.notify() //或者wait() } 
4,sleep必须捕获异常，而wait，notify和notifyAll不需要捕获异常

