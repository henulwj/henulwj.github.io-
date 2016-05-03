---
title: hexo+github搭建技术博客
date: 2016-04-18 20:54:21
tags: 
    - hexo
---

### 写在前面

之前用hexo搭建完github博客就想写一篇搭建的教程，一直没有写，一方面是网上有太多了，随便某度一下就可以找到一大堆。另一方面就是自己懒（无药可救了！！！）。最近一个同学来请教我怎么搭建的，我想还是有必要整理一下，把自己走过的路，遇到的坑记录一下！

<!-- more -->

#### 1. 基础准备

> - github账号
> - git
> - nodejs
> - hexo
> - markdown编辑器（非必须）

#### 2. 本地环境安装

> 本次搭建是在windows 7环境下搭建的，linux下也类似

a、 注册github账号，过程略过

b、 下载安装[mygit](https://git-scm.com/download/)，按照提示一步一步安装，安装过程略过

c、 安装完成后配置git用户名和邮件地址,对应你注册的github账号和邮箱

```shell
	git config --global user.name "username"
	git config --global user.email "username@example.com"
 
```

d、 本地生成ssh keys

```shell
	ssh-keygen -t rsa  -C "your_email@example.com" #简单的话，一路回车
```

e、github个人信息中添加ssh公钥，在`~/.ssh`找到生成id_rsa.pub文件,然后，在GitHub右上方点击头像，选择”Settings”，在右边的”Personal settings”侧边栏选择”SSH Keys”。接着粘贴公钥，点击”Add key”按钮。最后测试

```shell
	ssh -T git@github.com
```

f、 下载安装[nodejs](https://nodejs.org/en/download/)，安装过程略过，安装完成后在安装[hexo](http://hexo.io/zh-cn/),在控制台执行一下

```shell
	npm install hexo-cli -g
```

以上步骤完成基本安装就完成了，接下来进入配置阶段

#### 3. 配置部署hexo

a、 首先在自己的GitHub账号下创建一个新的仓库，命名为username.github.io（username是你的账号名),记得要在项目设置里面的Github Pages中点击`Launch automatic page generator`

b、 git clone仓库到本地

c、 在本地执行

```shell
	hexo init
	npm install
	hexo g
	hexo s #在本地4000端口查看
```

d、 部署到github上需要配置`_config.yml`

```
	deploy:
	  type: git
	  repo: git@github.com:/username/username.github.io.git
	  branch: master
```

还需要安装一个部署插件

```shell
	npm install hexo-deployer-git --save
```


e、 配置完成以后就可以部署了

```shell
	hexo g
	hexo d
```

f、写新文章可以使用如下命令

```shell
	hexo new "titlename" #在目录source/_post下产生对应名字的md文件
```

e、 还有更多相关配置、入更换主题、对文章分类等查看[hexo官网](https://hexo.io/zh-cn/)

#### 总结

终于写完了，过程不是很详细，但大体上流程就是这样，不是很难，自己动动手就能完成了。


#### 更多详细参考

1. [Hexo(一)：在GitHub上搭建静态博客](http://blog.hjtxxx.com/2015/08/13/Hexo-一-：在GitHub上搭建静态博客/)
2. [Hexo(二)：使用自己的域名访问博客](http://blog.hjtxxx.com/2015/08/18/Hexo-二-使用自己的域名访问博客/)
3. [Hexo(三)：同时部署到GitHub和GitCafe/](http://blog.hjtxxx.com/2015/08/18/Hexo-三-：同时部署到GitHub和GitCafe/)
4. [Hexo折腾记——性能优化篇](https://yq.aliyun.com/articles/8608)
5. [hexo主题](https://hexo.io/themes/)
6. [Hexo SEO优化](http://blog.csdn.net/zaoan_wx/article/details/50859675)