---
{"type":"blog","title":"017-Karabiner-Elements入门","tags":["blog/tutorial"],"categories":["技术教程","博客搭建"],"highlight_shrink":false,"toc_expand":false,"abbrlink":"3b767db4","establish":"2023-06-16 21:13:30","cover":null,"dg-publish":true,"permalink":"/Blog/017-Karabiner-Elements入门/","dgPassFrontmatter":true,"created":"2025-02-21T11:01:33.135+08:00","updated":"2025-03-03T20:51:24.722+08:00"}
---

[toc]


# 1. 一. 什么是 Karabiner-Elements？

Karabiner-Elements （下面我们简称为Karabiner）官网对自己的描述是 “A powerful and stable keyboard customizer for macOS.”，我使用下来的感受是 Karabiner-Elements 是 macOS 平台上一款非常强大的键位映射工具，没有吹嘘的成分，买家秀和卖家秀是一样的。

也就是我们可以自定义mac上的按键为任意按键及其组合,自定义快捷键。

1. **一些术语：**
- 左边的command键为`left_command`,右边的为`right-command`,其他按键同理。
- 返回键(ESC)键叫做escape,即逃跑的意思。
- 空格键叫做`spacebar`。
- 中英文切换键(也就是windows电脑的大小写切换键，即left_shift上面的那个)叫做`caps_lock`。

2. **注意事项**
- 调试工具(Mac实时显示键盘按键软件):[下载](https://github.com/keycastr/keycastr/releases)



# 2. 二. 若干示例(持续更新)

## 2.1. 将1个键映射成n个键的组合

以下步骤将实现以下效果：
如果点击`right_option`+ **`其他键`** 时，`right_option`将会映射成`left_command`+`left_option`; 
如果**单独**点击`right_option`，将会映射成`left_command`+`left_option`+`1`

1. 打开软件，选择`Complex Modifications`，点击`Add rule`
- <div style="text-align: left;">
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);
    width:75%; display: block; margin: 0;" 
    src="http://img.codertoro.top/Bucket/img/material/017-Karabiner-Elements%E5%85%A5%E9%97%A8/iShot_2023-06-16_21.39.59.jpg">
     </div>

2. 点击`Import more rules from the Internet (Open a web browser)`
- <div style="text-align: left;">
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);
    width:75%; display: block; margin: 0;" 
    src="http://img.codertoro.top/Bucket/img/material/017-Karabiner-Elements%E5%85%A5%E9%97%A8/iShot_2023-06-16_21.40.10.jpg">
     </div>

3. 搜索`Change caps_ lock key`,选择第一个，点击`import`
- <div style="text-align: left;">
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);
    width:75%; display: block; margin: 0;" 
    src="http://img.codertoro.top/Bucket/img/material/017-Karabiner-Elements%E5%85%A5%E9%97%A8/iShot_2023-06-16_21.41.04.jpg">
     </div>

4. 回到第二步的页面，选择`Change caps_lock to control if pressed with other keys, to escape if pressed alone`,点击`Enable`.
- <div style="text-align: left;">
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);
    width:75%; display: block; margin: 0;" 
    src="http://img.codertoro.top/Bucket/img/material/017-Karabiner-Elements%E5%85%A5%E9%97%A8/iShot_2023-06-16_21.41.25.jpg">
     </div>

5. 打开终端，`sudo su`进入管理员模式，编辑以下文件，`./config/karabiner/karabiner.json`,可以一层一层进入，避免出错。
- <div style="text-align: left;">
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);
    width:75%; display: block; margin: 0;" 
    src="http://img.codertoro.top/Bucket/img/material/017-Karabiner-Elements%E5%85%A5%E9%97%A8/iShot_2023-06-16_21.42.02.jpg">
     </div>

6. 将内容修改为如图所示。`esc`，`:wq`退出。
- <div style="text-align: left;">
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);
    width:75%; display: block; margin: 0;" 
    src="http://img.codertoro.top/Bucket/img/material/017-Karabiner-Elements%E5%85%A5%E9%97%A8/iShot_2023-06-16_22.31.26.jpg">
     </div>





