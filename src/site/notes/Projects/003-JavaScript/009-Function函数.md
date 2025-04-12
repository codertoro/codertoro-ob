---
{"type":"javascript","title":"009-Function函数","tags":["projects/javascript"],"author":"codertoro","establish":"2025-04-05","update":"2025-04-05","dg-publish":true,"categories":["数据类型","引用数据类型"],"permalink":"/Projects/003-JavaScript/009-Function函数/","dgPassFrontmatter":true,"created":"2025-04-05T20:20:16.421+08:00","updated":"2025-04-12T17:14:50.006+08:00"}
---

# 1. 函数的调用
- 直接调用
- 在表达式中调用
- 在超链接中调用
```html
<!DOCTYPE html>
<html>
<head>
  <title>调用 JS 函数示例</title>
  <script>
    function sayHello() {
      alert("你好，世界！");
    }
  </script>
</head>
<body>
  <a href="javascript:sayHello()">点击这里调用函数</a>
</body>
</html>
```
- 在事件中调用