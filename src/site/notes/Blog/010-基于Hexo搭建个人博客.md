---
{"type":"blog","title":"010-基于Hexo搭建个人博客","tags":["blog/tutorial"],"cover":"https://codertoro-img01.s3.ladydaily.com/img/material/%E5%9F%BA%E4%BA%8EHexo%E6%90%AD%E5%BB%BA%E4%B8%AA%E4%BA%BA%E5%8D%9A%E5%AE%A2.jpg","categories":["技术教程","博客搭建"],"abbrlink":"d90dd0c3","establish":"2023-01-13 22:37:33","dg-publish":true,"permalink":"/Blog/010-基于Hexo搭建个人博客/","dgPassFrontmatter":true,"created":"2025-02-21T11:01:33.123+08:00","updated":"2025-03-04T18:41:22.660+08:00"}
---

<!-- [toc] -->
# 1. 安装Node.js
前往官网www.nodejs.org 下载xx.xx.xx LTS(长期支持版本)

# 2. 打开终端

## 2.1. 进入管理员模式
``` bash
sudo su
#输入密码
```
<!--more-->

## 2.2. 检查版本
``` bash
node -v
npm -v
```
## 2.3. 下载cnpm
``` bash
npm install -g cnpm --registry=https//registry.npm.taobao.org
cnpm -v
```
## 2.4. 安装hexo
``` bash
cnpm install -g hexo-cli
hexo -v
```

# 3. 创建博客目录

## 3.1. 创建空文件夹
``` bash
mkdir myblog
```
注：myblog为文件夹名，可自定义

## 3.2. 初始化博客
``` bash
cd myblog
pwd
sudo hexo init
#耗时很长，耐心等待
#成功会在最后一行输出
#INFO start blogging with hexo
```

## 3.3. 启动博客
``` bash
hexo s
#复制4000端口的本地地址，在浏览器中打开
```

# 4. 写文章

## 4.1. 新建md文件
``` bash
hexo n "我的第一篇文章"
```
## 4.2. 开始写作

- 使用 [MarkDown](https://hx.dcloud.net.cn/Tutorial/Language/markdown) 语法
- 软件推荐:VSCode, HBuilderX, Typora(前两个免费，后一个也有免费版，我用的Typora，界面简洁)
- 嵌入[图片](https://codertoro.gitee.io/2022/09/07/%E5%9F%BA%E4%BA%8Egithub%E5%9B%BE%E7%89%87%E4%B8%8A%E4%BC%A0%E6%95%99%E7%A8%8B/)、[视频](https://codertoro.gitee.io/2022/09/06/%E8%A7%86%E9%A2%91%E4%B8%8A%E4%BC%A0%E5%88%9D%E7%BA%A7%E6%95%99%E7%A8%8B/)等方法请点击超链接

## 4.3. 生成预览
``` bash
#在myblog目录下执行以下命令
#清除缓冲（有害无益）
hexo clean
#生成
hexo g
#预览
hexo s
```
# 5. 部署到代码仓库
## 5.1. 新建仓库

**使用Github**
* 仓库名为：xxx.github.io(xxx为用户名)
* 仓库为public
* 将来访问地址为 xxx.github.io

**使用Gitee**
* 仓库名为：xxx(xxx为用户名)
* 仓库为public
* 将来访问地址为 xxx.github.io

## 5.2. 安装部署插件
``` bash
#在myblog目录下执行
cnpm install --save hexo-deployer-git
```

## 5.3. 配置_config.yml
``` bash
theme: yilia
# Deployment
## Docs: https://hexo.io/docs/one-command-deployment
deploy:
  #三个选项冒号后都用空格，无单引号
  type: git
  #在仓库代码下载/克隆处可以复制ssh或者https链接
  #1.https链接
  #需要每次hexo d 时输入用户名和密码
  #repository: https://gitee.com/codertoro/codertoro.git
  #2.ssh链接
  #需要进行配置，配置成功可以免密登录，即以后hexo d不需要输入用户名和密码
  repository: git@toscode.gitee.com:codertoro/codertoro.git
  #注意自己的分支是叫main还是master
  branch: master
```



## 5.4. 设置用户签名
``` bash
git config --global user.name "xxx"
git config --global user.email "xxx@xxx"
```

## 5.5. 一系列命令
``` bash
#清除缓存
hexo clean
#生成
hexo g
#预览
hexo s
#推送
hexo d
```

# 6. 设置yilia主题
``` bash
#下载主题
git clone https://github.com/litten/hexo-theme-yilia.git theme/yilia
#或者复制已有的yilia文件
#或者手动到github下载，可以安装插件来下载
```

# 7. 常见问题
## 7.1. github连接失败
GitHub是外网，访问速度慢，可以使用 [Steam++](https://steampp.net)进行加速，个人感觉比[uu加速器](https://uu.163.com/)的学术资源加速管用。不管怎么加速，访问速度还是不如gitee快，hexo d会经常出问题

## 7.2. gitee的缺点
gitee虽然访问速度快，但gitee pages只能使用xxx.gitee.io访问，不能设置个性化域名。只有gitee pages pro可以设置个性化域名，但目前(2023.1.13)已经暂停向个人用户购买gitee pages pro的服务，只有企业版可以购买和使用。

## 7.3. ssh免密登录
``` bash
#在终端超级用户下
git config --list
#如果没有用户名和密码，则需要执行下面两行
git config --global user.name "您的username"
git config --global user.email "xxx@qq.com" 
#开始生成ssh-keys
ssh-keygen -t rsa -C "xxx@xxx"
#连按三次回车，如果需要输yes/no,直接输入yes
#在Windows系统进入C:\Users\您的用户名\.ssh
#在macOS系统中进入/Users/您的用户名/.ssh
#右键git bash here
cat id_rsa.pub
```

* 复制公共ssh密钥




*  将ssh keys粘贴到账号中(在头像下设置里)




``` bash
#以下命令二选一
#验证是否成功（github）
ssh -T git@github.com
#验证是否成功（gitee）
ssh -T git@gitee.com
```
