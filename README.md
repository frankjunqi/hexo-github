
---
title: hexo + github 搭建个人免费博客
---
### hexo + github 搭建个人免费博客
你可能经常会看到类似于这样的博客：
![](http://upload-images.jianshu.io/upload_images/136678-4d36d1bd7d7c2f3c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](http://upload-images.jianshu.io/upload_images/136678-030253f986bbeca7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


##### 为什么要搭建个人博客 
###### 1:为了装逼
###### 2:个人博客更加自由，可以自定义成你想要的什么样子

#### 1.创建Github 域名和空间
##### 1.1注册
首先你需要注册一个Github账号,注册过程可能需要验证你的邮箱,注意username，这会影响到你的域名，你的域名将会是 username.github.io ，所以认真的取个名字吧。
##### 1.2 创建仓库
然后需要创建一个仓库(repository) 来存储我们的网站，点击首页任意位置出现的 New repository按钮创建仓库, Respository name 中的username.github.io 的username 一定与前面的Owner 一致，记住你的username下面会用到。

#### 2. 安装
Hexo 可以说是目前最流行的博客框架了，基于Nodejs，更多信息可以google，下面需要安装的工具包括 Git，Nodejs，Hexo。

##### 1.安装Git
	 // 如果已安装HomeBrew 无需执行此行
 	$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/	Homebrew/install/master/install)"
 	$ brew install git   // 安装Git	

##### 2.安装Nodejs
先安装nvm，这是Nodejs版本管理器，可以轻松切换Nodejs版本

 	1. Homebrew 安装方式，此安装方式无需重启
 	$ brew install nvm  
 	$ mkdir ~/.nvm
 	$ export NVM_DIR=~/.nvm
 	$ . $(brew --prefix nvm)/nvm.sh

安装完成后，重启终端 并执行下列命令即可安装 Node.js
	
	 $ nvm install 4
	 
##### 3.安装Hexo
以上所有都安装完成之后再安装Hexo
 	
 	$ sudo npm install hexo-cli -g
 	
所有必须工具已经安装完成，下面我们就可以生成博客，上传至我们的Github 仓库了。

#### 3. 编写，发布
接下来我们需要用Hexo初始化一个博客，然后更改一些自定义的配置，或者加上自己喜欢的主题，写上第一篇文章，然后发布到自己的个人Github网站(username.github.io)。

##### 1.创建博客
将下面的 username 替换成你自己的username(其实也无所谓，作者强迫症)，执行成功后，会创建出一个名为 username.github.io 的文件夹。

	$ hexo init username.github.io
	
##### 2.更改配置
###### 1.主题安装
为了使博客不太难看，我们需要安装一个主题，切换至刚刚生成的Hexo 目录，安装主题

	$ cd username.github.io
	$ git clone https://github.com/monniya/hexo-theme-new-vno themes/vno
	
###### 2.基础配置：
打开文件位置username.github.io/_config.yml修改几个键值对，下面把几个必须设置的列出来按需求修改，记得保存， 还有注意配置的键值之间一定要有空格

	 title: dimsky 的 9 维空间    //你博客的名字
	 author: dimsky  //你的名字
 	language: zh-Hans    //语言 中文
 	theme: next   //刚刚安装的主题名称
 	deploy:
   		type: git    //使用Git 发布
   		repo: https://github.com/username/username.github.io.git    // 刚创建的Github仓库
###### 3.主题配置：
主题配置文件在username.github.io/themes/next/_config.yml中修改

###### 4.写文章
所有基础框架都已经创建完成，接下来可以开始写你的第一篇博客了
在username.github.io/source/_posts下创建你的第一个博客吧，例如，创建一个名为FirstNight.md的文件，用Markdown大肆发挥吧，注意保存。

###### 5.测试
 
 	 $ hexo s
 	 
测试服务启动，你可以在浏览器中输入https://localhost:4000 访问了。

###### 6.安装hexo-deployer-git自动部署发布工具

	 $ npm install hexo-deployer-git --save
	 
###### 7.发布
测试没问题后，我们就生成静态网页文件发布至我们的Github pages 中。
   
   	$ hexo clean && hexo g && hexo d
   	
如果这是你的第一次，终端会让你输入Github 的邮箱和密码，正确输入后，骚等片刻，就会把你的博客上传至Github 了。以后在每次把博客写完后，执行一下这个命令就可以直接发布了

你的博客已经完成了，在浏览器中输入 http://usrename.github.io