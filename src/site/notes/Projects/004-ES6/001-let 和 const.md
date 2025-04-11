---
{"type":"es6","title":"001-let 和 const","tags":null,"author":"codertoro","establish":"2025-04-06","update":"2025-04-06","dg-publish":true,"permalink":"/Projects/004-ES6/001-let 和 const/","dgPassFrontmatter":true,"created":"2025-04-06T15:28:00.331+08:00","updated":"2025-04-07T22:26:07.324+08:00"}
---

# 1. let
- 变量不能重复声明
	- `let star = 1;`
	- `let star = 1;`
- 块儿级作用域
``` js
if else while for{
let girl = "小红";
}
console.log(girl);
```
- 不存在变量提升
```js
console.log(song)
let song = "恋爱达人"; //不允许在变量声明之前使用变量,var可以
```
- 不影响作用域链（子函数调用父函数的变量）
```js
**{**
let school = "尚硅谷";
fuction fn(){
	console.log(school);//可以正常调用
}
fn();
}
```
> [!warning]+ 关于变量提升的易错点
> ``` javascript
> let items = document.getElementsByClassName("item");
> //遍历并绑定事件
> for(let i=0;i<items.length;i++){   
> 	items[i].onclick = function(){
> 	//修改背景色,方法一
> 	this.style.background = "pink";
> 	//方法二
> 	items[i].style.background = "pink"; 
> }
> }
> ```
> **如果for循环中的let改成var，则方法二不可用，因为var会变量提升到全局，每次items[i]都是访问的items[items.length],而let不会变量提升，所以只会在当前循环的作用域中起作用，items[i]访问时，自己所在的作用域(点击事件的回调函数中，也就是离他最近的{})没有定义i，则向上级作用域调用，也就是for循环，可以调用成功。也就是for循环每一遍都会创建一个i，i值也不同。**

# 2. const
- **一定要赋初始值**
- 一般常量使用**大写**
- 常量的值**不能修改**
- 块儿级作用域（同let）
- 对于数组和对象的元素修改，不算做对常量的修改，**不会**报错
