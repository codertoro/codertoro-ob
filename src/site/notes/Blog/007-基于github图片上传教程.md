---
{"type":"blog","title":"007-基于github图片上传教程","tags":["blog/tutorial"],"cover":"https://codertoro-img01.s3.ladydaily.com/img/material/%E5%9F%BA%E4%BA%8Egithub%E5%9B%BE%E7%89%87%E4%B8%8A%E4%BC%A0%E6%95%99%E7%A8%8B.jpg","categories":["技术教程","博客搭建"],"abbrlink":"801a4907","establish":"2022-09-07 10:09:39","dg-publish":true,"permalink":"/Blog/007-基于github图片上传教程/","dgPassFrontmatter":true,"created":"2025-02-21T11:01:33.116+08:00","updated":"2025-03-03T20:52:29.982+08:00"}
---


{% note info flat %}由于博客引入新的图片样式，暂时弃用该博文所述方法{% btn '/2023/04/04/70c5d4ac.html', 新的图片格式, far fa-hand-point-right,blue %}{% endnote %}
# 1. 网站工具

[图片上传 | PicX 图床神器 (xpoet.cn)](https://picx.xpoet.cn/#/upload)

[GitHub](https://github.com/)

# 2. 上传图片
1. 注册登录github账户

<!--more-->

2. 创建一个新的仓库

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img.codertoro.top/Bucket/img/material/007-%E5%9F%BA%E4%BA%8Egithub%E5%9B%BE%E7%89%87%E4%B8%8A%E4%BC%A0%E6%95%99%E7%A8%8B/Untitled.png" width = "50%"  alt="创建一个新的仓库" title="创建一个新的仓库"/>
</center>


3. 获取github token(第4-9步)

4. 点击头像处settings

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img.codertoro.top/Bucket/img/material/007-%E5%9F%BA%E4%BA%8Egithub%E5%9B%BE%E7%89%87%E4%B8%8A%E4%BC%A0%E6%95%99%E7%A8%8B/Untitled%201.png" width = "18%" height="50%" alt="点击头像处settings" title="点击头像处settings"/>
</center>


5. 点击developer settings

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img.codertoro.top/Bucket/img/material/007-%E5%9F%BA%E4%BA%8Egithub%E5%9B%BE%E7%89%87%E4%B8%8A%E4%BC%A0%E6%95%99%E7%A8%8B/Untitled%202.png" width = "50%" height="50%" alt="点击developer settings" title="点击developer settings"/>
</center>


6. 点击personal access tokens

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img.codertoro.top/Bucket/img/material/007-%E5%9F%BA%E4%BA%8Egithub%E5%9B%BE%E7%89%87%E4%B8%8A%E4%BC%A0%E6%95%99%E7%A8%8B/Untitled%203.png" width = "65%" height="50%" alt="点击personal access tokens" title="点击personal access tokens"/>
</center>


7. 点击generate a personal tokens

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img.codertoro.top/Bucket/img/material/007-%E5%9F%BA%E4%BA%8Egithub%E5%9B%BE%E7%89%87%E4%B8%8A%E4%BC%A0%E6%95%99%E7%A8%8B/Untitled%204.png" width = "60%" height="50%" alt="点击generate a personal tokens" title="点击generate a personal tokens点击generate a personal tokens"/>
</center>


8. 随便输入英文名字，权限都给上(其实有repo就够了)

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img.codertoro.top/Bucket/img/material/007-%E5%9F%BA%E4%BA%8Egithub%E5%9B%BE%E7%89%87%E4%B8%8A%E4%BC%A0%E6%95%99%E7%A8%8B/Untitled%205.png" width = "50%" height="50%" alt="设置名字和权限" title="设置名字和权限"/>
</center>


9. 点击generate，生成并复制github token(只出现一次，请妥善保存)

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img.codertoro.top/Bucket/img/material/007-%E5%9F%BA%E4%BA%8Egithub%E5%9B%BE%E7%89%87%E4%B8%8A%E4%BC%A0%E6%95%99%E7%A8%8B/Untitled%206.png" width = "35%" height="50%" alt="生成github token" title="生成github token"/>
</center>


10. 将github token输入到picx的配置中

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img.codertoro.top/Bucket/img/material/007-%E5%9F%BA%E4%BA%8Egithub%E5%9B%BE%E7%89%87%E4%B8%8A%E4%BC%A0%E6%95%99%E7%A8%8B/Untitled%207.png" width = "50%" height="50%" alt="picx配置" title="picx配置"/>
</center>


11. 根据提示选择仓库和命名方式，完成配置

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img.codertoro.top/Bucket/img/material/007-%E5%9F%BA%E4%BA%8Egithub%E5%9B%BE%E7%89%87%E4%B8%8A%E4%BC%A0%E6%95%99%E7%A8%8B/Untitled%208.png" width = "50%" height="50%" alt="选择仓库和命名方式" title="选择仓库和命名方式"/>
</center>


12. 将要上传的图片拖拽如picx中，点击上传即可得到图片外链(不手动删除仓库中的图片的话，外链永久有效)

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img.codertoro.top/Bucket/img/material/007-%E5%9F%BA%E4%BA%8Egithub%E5%9B%BE%E7%89%87%E4%B8%8A%E4%BC%A0%E6%95%99%E7%A8%8B/Untitled%209.png" width = "50%" height="50%" alt="上传图片" title="上传图片"/>
</center>


# 3. 开启github page

## 3.1. 方法

1. 进入创建仓库中的setting，点击page

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img.codertoro.top/Bucket/img/material/007-%E5%9F%BA%E4%BA%8Egithub%E5%9B%BE%E7%89%87%E4%B8%8A%E4%BC%A0%E6%95%99%E7%A8%8B/Untitled%2010.png" width = "50%" height="50%" alt="进入page" title="进入page"/>
</center>


2. 选择主分支main，选择相应目录(根目录即可),点击save

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img.codertoro.top/Bucket/img/material/007-%E5%9F%BA%E4%BA%8Egithub%E5%9B%BE%E7%89%87%E4%B8%8A%E4%BC%A0%E6%95%99%E7%A8%8B/Untitled%2011.png" width = "40%" height="50%" alt="选择相应目录" title="选择相应目录"/>
</center>


3. 等待1-2分钟，刷新页面就可以看到地址了(不可以直接访问，想直接访问仓库名必须为用户名.github.io，如笔者的coder-ox.github.io,这是个人博客地址，和图片仓库地址是两码事)

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img.codertoro.top/Bucket/img/material/007-%E5%9F%BA%E4%BA%8Egithub%E5%9B%BE%E7%89%87%E4%B8%8A%E4%BC%A0%E6%95%99%E7%A8%8B/Untitled%2012.png" width = "70%" height="50%" alt="得到地址" title="得到地址"/>
</center>


## 3.2. 用法

1. 将图片上传到图片仓库之后，在github仓库中找到目标图片,复制路径

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img.codertoro.top/Bucket/img/material/007-%E5%9F%BA%E4%BA%8Egithub%E5%9B%BE%E7%89%87%E4%B8%8A%E4%BC%A0%E6%95%99%E7%A8%8B/Untitled%2013.png" width = "50%" height="50%" alt="复制图片路径" title="复制图片路径"/>
</center>


2. 在浏览器地址栏输入“个人博客地址+刚刚复制路径”(例如[https://coder-ox.github.io/image_hosting/20220906/2022年8月12日.4mhf6pemlqg0.webp](https://coder-ox.github.io/image_hosting/20220906/2022年8月12日.4mhf6pemlqg0.webp))，即可在线预览图片(前提是成功搭建个人博客网站)

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://img.codertoro.top/Bucket/img/material/007-%E5%9F%BA%E4%BA%8Egithub%E5%9B%BE%E7%89%87%E4%B8%8A%E4%BC%A0%E6%95%99%E7%A8%8B/Untitled%2014.png" width = "75%" height="50%" alt="在线预览图片" title="在线预览图片"/>
</center>


# 4. 代码嵌入

1. 根据[《hexo搭建博客》](https://coder-ox.github.io/2022/02/23/hexo%E6%90%AD%E5%BB%BA%E5%8D%9A%E5%AE%A2/)中的教程创建草稿

2. 获取链接方法：

​		由***二.12***获取 *Staticaly CDN 外链* 或 *Cloudflare CDN 外链*  (更方便)

​		由***三.2*** 手动输入地址

3. Typora: 右键插入图像(ctrl+shift+I)

4.Markdown: 格式如下(我的#pic_center不好使，加了也无法居中)

```markdown
![图片描述](图片地址#pic_center)
```

- 使用div标签(目前不会设置图注)：

```html
<div align="center"> <img src=https://cdn.staticaly.com/gh/coder-ox/image_hosting@master/20220908/伊拉克难民.1cnvyrfnjmbk.webp alt="alt" title="title"/> <!--alt用于图片无法加载时显示图片名称，title用于鼠标在图片上悬停时显示图片名称，理论上二者内容一致-->
  <!--换行-->
 <br>
  <!--图注(和图像在同一个div中，不会错乱)-->
 <div style="color:orange; border-bottom: 1px solid #d9d9d9;
 display: inline-block;
 color: #999;
 padding: 2px;">伊拉克难民</div>
</div>
```

- 使用center标签（有图注）:

```html
<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://cdn.staticaly.com/gh/coder-ox/image_hosting@master/20220908/8cbc97c5af285e853f20736bb242936.gkt1hezvqio.webp" width = "50%"  alt="创建一个新的仓库" title="创建一个新的仓库"/> <!--width可以将长宽等比例缩放，alt用于图片无法加载时显示图片名称，title用于鼠标在图片上悬停时显示图片名称，理论上二者内容一致-->
    <!--换行-->
    <br>
     <!--图注(和图像在同一个div中，不会错乱)-->
    <div style="color:orange; border-bottom: 1px solid #d9d9d9;
    display: inline-block;
    color: #999;
    padding: 2px;">
      创建一个新的仓库
  	</div>
</center>
```

5. 实例图片([来源](http://bz.heze.cn/html/2016-10/27/content_3_12.htm),*侵删*)：	

<center>
    <img style="border-radius: 0.3125em;
    box-shadow: 0 2px 4px 0 rgba(34,36,38,.12),0 2px 10px 0 rgba(34,36,38,.08);" 
    src="https://cdn.staticaly.com/gh/coder-ox/image_hosting@master/20220908/伊拉克难民.1cnvyrfnjmbk.webp " title="伊拉克难民">
</center>
