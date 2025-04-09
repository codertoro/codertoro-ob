---
{"type":"jquery","title":"001-JQuery选择器","tags":null,"author":"codertoro","establish":"2025-04-08","update":"2025-04-08","dg-publish":true,"permalink":"/Projects/JQuery/001-JQuery选择器/","dgPassFrontmatter":true,"created":"2025-04-08T17:12:03.257+08:00","updated":"2025-04-08T21:31:02.754+08:00"}
---

# 1. JQuery
- JQuery 是一个js库，简化js编程，更容易操作HTML文档，处理事件
# 2. 基础语法
- JQuery 入口
```javascript
$(document).ready(function(){
	//jQuery 代码写在这里
})
//简写形式
$(function(){
	//写这里
})
```
# 3. 基本选择器
- id选择器
- 类选择器
- 标签选择器
- 通配选择器
- 组合选择器（并集选择器）
- 组选择器（选择多个）
```html
<div class="c" id="box">
	<p></p>
	<p></p>
	<p></p>
</div>
<p id="p1"></p>
<script>
	$(function(){
	//写这里
	$("#box"); //id选择器
	$(".c");   //类选择器
	$("div");  //标签选择器
	$("*");    //通配选择器
	$(".c,p");     //组合选择器,并集
	$("div p");     //组选择器 ,选择div的所有后代p
})
</script>
```
# 4. 层次选择器
- 后代选择器
- 子选择器
- 相邻兄弟选择器
- 兄弟选择器
# 5. 基本过滤选择器
- `:first` 
- `:last`
- `:eq(index)` 索引从0开始
- `:gt(index)` 选择索引大于index的元素
- `:lt(index)` 选择索引小于index的元素
- `:even` 索引为偶数 
- `:odd` 索引为奇数
- `:not(selector)` 排除
# 6. 可见性过滤选择器
- `:visible` 
- `:hidden`
- **注意：** 什么时候`hidden` 会被选中，自身或父元素的样式存在以下值**之一**：
```css
/* 情况1 */
display:none;
/* 情况2 */
opacity: 0;
/* 情况3 */
visibility: hidden;
```
# 7. 子元素选择器
- `:first-child`
- `:last-child`
- `:nth-child(n)`
- `:nth-last-child(n)`
- `:only-child`
# 8. 表单属性状态过滤器
- `:enabled`  选取所用启用的表单
- `:disabled`
- `:checked`
- `:selected`
> [!warning]+ :first和:first-child的区别
运算顺序不一样：
```html
//示例1
<ul>
  <div>标题</div>
  <li>🍎 苹果</li>
  <li>🍌 香蕉</li>
</ul>
```
- `$("ul li:first")` 选中的是`<li>🍎 苹果</li>`
- `$("ul li:first-child")` **无法选中任何一个li** ,因为没有一个`li`是`ul` 的第一个孩子
```html
<ul class="fruit-list">
  <li>苹果</li>
  <li>香蕉</li>
  <li>橘子</li>
</ul>
<ul class="color-list">
  <li>红色</li>
  <li>绿色</li>
  <li>蓝色</li>
</ul>
<script>
  $(function () {
    const v1 = $("ul li:first")
    const v2 = $("ul li:first-child")
    console.log(v1.get()) //
    console.log(v2.get())
  })
</script>
```

