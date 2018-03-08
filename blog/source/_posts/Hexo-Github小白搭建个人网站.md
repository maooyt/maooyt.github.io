---
title: Hexo+Github小白搭建个人网站
date: 2018-03-08 15:13:04
tags: TechBlog

---



## 前言：

​        本文参考网上相关教程，初步分析每一步的原因，并结合实际使用情况，尽可能详尽地写出网站搭建的过程。

## GitHub创建个人仓库

**说明**：Hexo框架里所有文件需要放在GitHub里，因此有一个GitHub仓库是前提。

1.打开https://github.com/链接，进入GitHub注册页面，填写用户名等信息 ，点击Sign up for GitHub按钮，按照Step1，Step2，Step3完成注册过程。

![ 博客1 01](http://p4wix1t4z.bkt.clouddn.com/image/png/%E5%8D%9A%E5%AE%A21%2001.png)

Step1:

![博客1 02](http://p4wix1t4z.bkt.clouddn.com/image/png/%E5%8D%9A%E5%AE%A21%2002.PNG)

Step2:直接点击Continue

![博客1 03](http://p4wix1t4z.bkt.clouddn.com/image/png/%E5%8D%9A%E5%AE%A21%2003.PNG)

Step3：几个问题可以不填，直接点Submit按钮。

![博客1 05](http://p4wix1t4z.bkt.clouddn.com/image/png/%E5%8D%9A%E5%AE%A21%2005.png)

出现如下界面，说明注册成功！

![博客1 06](http://p4wix1t4z.bkt.clouddn.com/image/png/%E5%8D%9A%E5%AE%A21%2006.PNG)

2.按照以下步骤新建个人仓库（repo）【repo用于存放博客相关的文件】

Step1：

![博客1 07](http://p4wix1t4z.bkt.clouddn.com/image/png/%E5%8D%9A%E5%AE%A21%2007.png)

Step2：邮件认证。

![博客2 08](http://p4wix1t4z.bkt.clouddn.com/image/png/%E5%8D%9A%E5%AE%A22%2008.png)

Step3:进入注册邮箱，会看到Github发送的邮件。

![博客1 09](http://p4wix1t4z.bkt.clouddn.com/image/png/%E5%8D%9A%E5%AE%A21%2009.PNG)

Step:点击认证邮件中的链接。

![博客1 10](http://p4wix1t4z.bkt.clouddn.com/image/png/%E5%8D%9A%E5%AE%A21%2010.png)

Step4：认证成功！

![博客1 12](http://p4wix1t4z.bkt.clouddn.com/image/png/%E5%8D%9A%E5%AE%A21%2012.png)

Step5:新建仓库

![博客1 13](http://p4wix1t4z.bkt.clouddn.com/image/png/%E5%8D%9A%E5%AE%A21%2013.png)

![博客1 14](http://p4wix1t4z.bkt.clouddn.com/image/png/%E5%8D%9A%E5%AE%A21%2014.png)

Step6:新建一个分支

**说明：**发布后生成的文件要放在GitHub上的，这样才能通过域名访问；把源文件也放上去是方便在其他电脑上更新博客源文件并进行发布等操作，因此为了使用方便，新建一个分支。

原来项目有一个默认分支master，再新建一个分支，分支名可以为hexo，将其设置为默认分支。两个分支分别用来放不同的文件，master用来放博客发布时生成的HTML等文件，hexo分支用于放博客源文件。



## 安装git

**说明：** 

1. git是类似svn的版本控制工具，与github不是一个软件。

2. 为什么要设置ssh秘钥

   尝试下：如果不设置公钥 推送代码时要一致输入账号和密码吗

   为了省去每次输入账号密码，采用ssh。推送时，git会匹配电脑里的私钥和Github里的公钥，如果匹配就认为你是合法用户，则允许推送。

Step1：从Git官网（https://git-scm.com/）上下载安装包并安装。

![博客1 15](http://p4wix1t4z.bkt.clouddn.com/image/jpeg/%E5%8D%9A%E5%AE%A21%2015.jpg)

Step2：测试是否安装成功。当在电脑桌面上右击菜单里有Git GUI Here 和Git Bash Here时，说明安装成功。

![博客1 16](http://p4wix1t4z.bkt.clouddn.com/image/png/%E5%8D%9A%E5%AE%A21%2016.PNG)

Step3：将Git和Github账号绑定。

鼠标右击在列表中点击Git Bash Here。输入以下命令，设置user.name和user.email配置信息：

```
git config --global user.name "你的GitHub用户名"
git config --global user.email "你的GitHub注册邮箱"
```

生成ssh秘钥文件：

```
ssh-keygen -t rsa -C "你的GitHub注册邮箱"
```

然后直接三个回车即可，默认不需要设置密码，看到如图所示图像，说明ssh key已经生成了，共2个文件，地址在红框标记的地方。

![博客1 17](http://p4wix1t4z.bkt.clouddn.com/image/png/%E5%8D%9A%E5%AE%A21%2017.png)

找到生成的.ssh的文件夹中的id_rsa.pub文件，将内容全部复制

打开[GitHub_Settings_keys](http://link.zhihu.com/?target=https%3A//github.com/settings/keys) 页面，新建new SSH Key。

Step1：打开github页面右上角的个人头像，点击settings

![博客1 18](http://p4wix1t4z.bkt.clouddn.com/image/png/%E5%8D%9A%E5%AE%A21%2018.png)

Step2:页面左侧，点击SSH andGPG keys

![博客1 19](http://p4wix1t4z.bkt.clouddn.com/image/png/%E5%8D%9A%E5%AE%A21%2019.png)

Step3:

![博客1 20](http://p4wix1t4z.bkt.clouddn.com/image/png/%E5%8D%9A%E5%AE%A21%2020.png)

Step4：

![博客1 21](http://p4wix1t4z.bkt.clouddn.com/image/png/%E5%8D%9A%E5%AE%A21%2021.png)

Step5：成功！

![博客1 22](http://p4wix1t4z.bkt.clouddn.com/image/png/%E5%8D%9A%E5%AE%A21%2022.png)

Step6：检测公钥是否设置成功。在Git Bash中输入命令 ssh git@github.com，出现如图所示提示，则成功。

![博客1 23](http://p4wix1t4z.bkt.clouddn.com/image/png/%E5%8D%9A%E5%AE%A21%2023.png)



## 安装node.js

**说明：**hexo的安装必须要有node.js环境，而部署和浏览不需要。
注意安装Node.js会包含环境变量及npm的安装，npm是node的模块管理器，只要一行命令就可以安装别人写好的模块，后面安装hexo的时候会用到该命令。

## 安装hexo

hexo是个人博客网站的框架，也就是上面所说的源文件，将其放在github项目hexo分支下。

Step1：clone Github项目到本地，新建分支

1.找到个人仓库地址（注意是ssh地址）

![博客1 26](http://p4wix1t4z.bkt.clouddn.com/image/png/%E5%8D%9A%E5%AE%A21%2026.png)

2.进入你想放项目的磁盘，右键点击git bash 输入git clone 你的项目地址。本地会生成一个与代码仓库同名的空文件夹。

![博客1 25](http://p4wix1t4z.bkt.clouddn.com/image/png/%E5%8D%9A%E5%AE%A21%2025.png)

3.新建分支

依次输入以下命令，新建分支hexo

在本地创建新的分支 git branch 分支名

将新的分支推送到github  git push origin 分支名

![博客1 27](http://p4wix1t4z.bkt.clouddn.com/image/png/%E5%8D%9A%E5%AE%A21%2027.png)



4.切换到hexo分支

切换到新的分支   git checkout 分支名

![博客1 28](http://p4wix1t4z.bkt.clouddn.com/image/png/%E5%8D%9A%E5%AE%A21%2028.png)

Step2：进入本地项目文件夹，使用npm命令安装hexo

```
npm install -g hexo-cli 
```

Step3：初始化博客

```
hexo init blog
```

因为hexo必须部署在空文件夹下，此处新建一个文件夹blog

至此，我们的个人博客网站已经在本地搭建好了。

## 推送网站

为了能让更多人访问我们的网站，我们需要发布到GIthub上。

Step1：修改配置文件

打开站点的配置文件_config.yml（也就是项目文件夹中的_config.yml文件），翻到最后修改为：

deploy: 
type: git
repo: 这里填入GitHub上创建仓库的完整路径（注意是ssh格式，见截图）
branch: master

![博客1 29](http://p4wix1t4z.bkt.clouddn.com/image/png/%E5%8D%9A%E5%AE%A21%2029.png)



Step2：安装Git部署插件

进入blog文件夹

```
npm install hexo-deployer-git --save
```

Step3：网站发布

```
hexo clean 
hexo g 
hexo d
```

Step4：浏览自己的网站

打开浏览器，在地址栏输入你的放置个人网站的仓库路径，即 [http://xxxx.github.io](http://link.zhihu.com/?target=http%3A//xxxx.github.io) ，至此，别人都能访问你的网站了。

## 更新你的第一篇博客

Step1：下载MarkDown编辑器，按照你想要的格式写下第一篇博客。

Step2：把编辑完成的.md文件放到blog\source\_post文件夹下

step3：输入命令，发布网站。

  先发布 执行hexo g -d生成网站并部署到GitHub上。

  再上传文件 依次执行git add .、git commit -m "..."、git push origin hexo提交网站相关的文件；

 

## 个性化博客

### 更改主题

进入blog目录 右击打开命令窗口输入命令：

```
git clone https://github.com/iissnan/hexo-theme-next themes/next
```

此时你的\blog\theme文件夹下多了名为 next 的文件夹 这就是next主题

![博客1 30](http://p4wix1t4z.bkt.clouddn.com/image/png/%E5%8D%9A%E5%AE%A21%2030.png)

打开_config.yml配置文件，修改主题为next

![博客1 31](http://p4wix1t4z.bkt.clouddn.com/image/png/%E5%8D%9A%E5%AE%A21%2031.png)



## 另一台电脑更新博客

同样新建文件夹 clone项目  通过Git bash依次执行npm install hexo、npm install 和 npm install hexo-deployer-git
完成。



## 常用的Git命令

git clone 你的github项目地址  克隆项目

git add . 增加本地文件到暂存区

git commit -m "提交日志" 提交代码

git push origin hexo 推送到远程hexo分支

git pull origin hexo 更新本地代码



## 常用的Hexo 命令

hexo n "你想新建的博客名"

hexo clean 本地清除缓存

hexo g 生成网站

hexo d 发布网站



## error可能原因：

1. ERROR Process failed: _posts/Hexo-Github小白搭建个人网站.md
   YAMLException: can not read a block mapping entry; a multiline key may not be an implicit key at line 4, column 1

   **原因**：the reason is that there is not a space between `tags` and tag name. like this
   `tags:PHP` ==> `tags: PHP`




## 参考文章：

1. https://zhuanlan.zhihu.com/p/26625249 作者：吴润
2. https://www.zhihu.com/question/21193762 作者:CrazyMilk
3. https://hexo.io/zh-cn/docs/index.html hexo官方文档
4. https://www.jianshu.com/p/ada6b90f0f2e 作者：droidlover
5. https://www.cnblogs.com/hope-markup/p/6679564.html 作者：前端段子手
6. https://www.jianshu.com/p/0b1fccce74e0 作者：Michaelhbjian
7. https://newsn.net/say/hexo-blog-install.html 作者：sunan
8. http://www.ruanyifeng.com/blog/2016/01/npm-install.html 作者：阮一峰

