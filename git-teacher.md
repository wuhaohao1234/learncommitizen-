# git教程

## 安装git

* windows
    在Windows上使用Git，可以从[Git官网](https://git-scm.com/downloads)直接下载安装程序然后下一步，下一步，最后鼠标右击点击**Git Bash Here**(windows电脑记得在安装时勾选添加到环境变量)
* mac
    1. 安装homebrew，然后通过homebrew安装Git，具体方法请参考homebrew的文档：http://brew.sh/。

    2. 推荐直接从AppStore安装Xcode，Xcode集成了Git，不过默认没有安装，你需要运行Xcode，选择菜单“Xcode”->“Preferences”，在弹出窗口中找到“Downloads”，选择“Command Line Tools”，点“Install”就可以完成安装了。

## github官网

### 一、与github建立联系

github官网过登陆与注册(这个自己搞),然后登陆github在Repositories里面可以通过new创建自己的个人仓库

1. 第一栏Repository name是仓库名称
2. Description是仓库描述
3. 第三栏public是仓库是公有的，所有人都可以看
4. 第四栏是Private，私有仓库，只有规定的人才可以看到
5. Initialize this repository with a README是否添加readme.md说明文件，一般都选择是
6. Add .gitignore是否添加.gitignore文件，这个文件自己也可以创建，想一些不想上次的文件可以卸载里面，这个后面说
7. Add a license:是否添加协议,例如MIT协议

接下来是本地与github建立联系

1. 打开下载好的gitbash输入以下命令(后面双引号是创建github的邮箱，qq邮箱什么的)
`ssh-keygen-t rsa-C "your_email@youremail.com"`

    之后会有一些简单的让你确认的操作，之后让你会提示操作路径、密码等等，一般情况下就直接按回车一路过就可以。
完成后的图片
<center>

![img](https://img-blog.csdn.net/20170912222716512?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvSGFuYW5pX0ppYQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

</center>

2. 与github确认密钥

    windows电脑在c盘/用户/里面有个.ssh文件夹(一般默认是隐藏的，需要自己设置让它显示，自行百度)
    ![img](https://img-blog.csdn.net/20170912222924652?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvSGFuYW5pX0ppYQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)
    用github打开id_rsa,这是本机的密钥
    
3. 将本机密钥放在github里面,让github认识自己的电脑

    进人在github的Account settings(设置页面)头像右上角,然后点击左边的SSH and GPG keys，点击右下角new GPG key,设置名称title(随意),然后将本机的密钥粘贴上去,保存

4. 本机电脑确认

    本机电脑打开gitbash输入

    `ssh -T git@github.com`

    检查是否绑定,会提示continue，输入yes后继续，最后设置github全局的名称与邮箱(必须与gitbub同步)


```
git config --global user.name "名称"
git config --global user.email "邮箱"
```

## git命令常用操作

1. 将项目克隆在本地

在远程github项目中，右边有个clone download按钮，点击按钮得到远程地址，复制

`git clone 远程项目地址`

这样可以把远程的项目克隆在本地进行操作

### 一、git核心

    在git中有三个概念:暂存区，版本库，git官网中的代码

1. 当我对于文件进行编辑，然后我要将编辑后的文件添加到暂存区

`git add 文件名`

`git add -A`或`git add .`添加所有文件

如果我要比较当时的文件与暂存区文件的不同

`git diff`

如果我想知道当前的文件哪些和暂存区文件不一样的(指新增加的文件，删除的文件，改动的文件)

`git status`

2. 将暂存区文件添加到版本库

`git commit -m "文件描述信息message"`

这里关于commit描述信息message请参考[链接](https://github.com/wuhaohao1234/learncommitizen-)

这里先不说版本回退,但是记住一点**在git中文件的版本就是个时间轴，我在上一个时间的版本是可以找到的**

* 目前不需要掌握的：

上文中提到git就是个时间轴，假设有好多个人开发同一个代码，每个人称为一个分支(A与B分支)，A分支上面也没有做，只是B分支修改提交到版本库，这个时候与A分支没有任何关系，但是此时文件处在B分支最后一次的版本中，A就可以合并(merge)B分支的代码。这个时候A分支与B分支就都处于最新的版本

3. 将本地代码的最新分支上传到github上面

`git push`

这属于最简单的，但是github上面也可以有好多个分支，好多个人在开发，每个分支的文件又不同，所有其它分支的人需要首先向主分支发送一个请求(pr pull request)

`git pull`

然后再git push(这里严格来说应该push到你自己在github上面的分支上)

`git push origin 自己的分支`

4. 当代码上传后，向主分支发送pr，让主分支看你的代码是否符合要求，符合要求后，主分支会合并你的diamond
    点击new pull request
