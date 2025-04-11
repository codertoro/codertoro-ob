---
{"type":"blog","title":"025-解决插件Opener的一个小bug","tags":null,"author":"codertoro","establish":"2025-04-11","update":"2025-04-11","dg-publish":true,"permalink":"/Blog/025-解决插件Opener的一个小bug/","dgPassFrontmatter":true,"created":"2025-04-11T16:00:28.818+08:00","updated":"2025-04-11T16:09:39.427+08:00"}
---

Obsidian 的插件opener 可以让鼠标左键单击文件默认在问tab中打开，这一点在obsidian中无法设置。
但是opener存在一个小问题，已经打开的文件再次点击无法跳转回去。
- 解决方法：
	- 打开opener的js文件![](https://img.codertoro.top/Bucket/Blog/20250411160444688.png)
	- 找到如图所示的代码部分![](https://img.codertoro.top/Bucket/Blog/20250411160745960.png)
	- 更改为如下代码
<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">




```js
if (matchingLeaves.length) {
// 关闭空标签页（如果存在）
if (preparedEmptyLeave) {
this.detach();
}
// 聚焦到已存在的标签页
app.workspace.setActiveLeaf(matchingLeaves[0], { focus: true });
return oldOpenFile.apply(matchingLeaves[0], [file, openState]);
}
```

</div></div>

```js
if (matchingLeaves.length) {
// 关闭空标签页（如果存在）
if (preparedEmptyLeave) {
this.detach();
}
// 聚焦到已存在的标签页
app.workspace.setActiveLeaf(matchingLeaves[0], { focus: true });
return oldOpenFile.apply(matchingLeaves[0], [file, openState]);
}
```
