---
{"type":"jquery","title":"get()方法详解","tags":null,"author":"codertoro","establish":"2025-04-08","update":"2025-04-08","dg-publish":true,"permalink":"/Projects/005-JQuery/get()方法详解/","dgPassFrontmatter":true,"created":"2025-04-08T14:55:48.869+08:00","updated":"2025-04-12T17:47:43.956+08:00"}
---

- **JQuery** 一个提供丰富的元素操作函数的javascript库
# 1. 给出以下代码
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <ul>
      <li>1</li>
      <li>2</li>
      <li>3</li>
      <li>4</li>
    </ul>
    <script
      src="https://code.jquery.com/jquery-3.7.1.js"
      integrity="sha256-eKhayi8LEQwp4NKxN+CfCh+3qOVUtJn3QNZ0TciWLP4="
      crossorigin="anonymous"
    ></script>
    <script>
      $(function () {
        // let arr = $("ul li").map(function(){
        // return $(this).text();
        // })
        // console.log(typeof(arr));
        let arr = $("ul li")
        console.log(arr)
        console.log(...arr)   //第一种
        console.log([...arr])   //第二种
        console.log(Array.from(arr))  //第三种
        console.log(arr.get())  //第四种
      })
      // let a = ["aa","bb","cc"];
      // console.log(...a)
    </script>
  </body>
</html>

```
- 这里有四种类似的拆分方式
- 第一种：**扩展运算符** `...`
- **JQuery对象本省并不是iterable(可迭代)对象** ，所以这种方式可能会报错。不过，现代浏览器中，JQuery对象其实是“伪数组”结构，`...arr` 实际上展开的是里面的DOM元素，如图所示：

![|482](https://img.codertoro.top/Bucket/Projects/JQuery/202504081523718.png)

- 第二种：**展开运算符** [...Array]
- 原生DOM的方法，尝试将JQuery对象转化成数组。但是，转换后的数组的每项依旧是JQuery封装过的DOM。

![|439](https://img.codertoro.top/Bucket/Projects/JQuery/202504081527790.png)

- 第三种：**Array.from()**
- 原生DOM的方法，效果和第二种一样，依旧不是纯DOM数组
![|433](https://img.codertoro.top/Bucket/Projects/JQuery/202504081529611.png)
- 第四种：**get(index)**  index为索引值
- JQuery对象的函数，返回一个原生DOM数组
![|438](https://img.codertoro.top/Bucket/Projects/JQuery/202504081531225.png)
- 第五种：**$.makeArray(object)** 返回一个数组，object为对象
# 2. 验证方法
```javascript
let a1 = arr.get();
let a2 = [...arr];
console.log(a1[0] instanceof HTMLElement); // true
console.log(a2[0] instanceof HTMLElement); // false（可能）
console.log(a2[0] instanceof JQuery); 
```
