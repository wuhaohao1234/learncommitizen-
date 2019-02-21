# 学习git中的commit格式规范

## 解决的问题

* 优雅的提交commit message(提交信息)

## 文档(这里采用angularcommit格式规范)

### 1、package.json中version版本的规范

#### 基本格式

主版本号（Major）.次版本号（Minor）.修订号（Patch）

1. 0.0.1例如修改文档，样式，格式。对于全局代码无影响的小操作
2. 0.1.0例如新增加一个功能，修复一个bug，对于全局代码有较小的影响
3. 1.0.0例如全局代码的重构，直接改变全局代码

### 2、如何写commit message(这里采用Angular commit格式规范)

#### 规范的书写方式
1. 头部head
```
type:说明提交的类型 = {
    feat:增加一个新的功能,
    fix:修补bug,
    docs:修改文档,
    style:修改样式,
    refactor:重构,
    test:测试,
    chore:构建过程辅助工具的变动
}
scope:用于说明 commit 影响的范围，比如数据层、控制层、视图层等等，视项目不同而不同
subject：commit 目的的简短描述，不超过50个字符。
```
2. body
    对于提交的详细描述
3. footer
    不兼容变动，关闭 Issue

### 3、使用工具Commitizen

1. 全局安装Commitizen

`npm install -g commitizen cz-conventional-changelog`

    这里要改动全局git下的.czrc文件(不介意全局安装)

2. 本地安装(推介)

`npm install -D commitizen cz-conventional-changelog`

3. 配置package.json

```
{
  "name": "项目名称",
  "version": "版本号",
  "description": "项目描述",
  "main": "入口文件",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "commit": "git-cz"  //新建commit命令
  },
  "config": {   //新建config配置，将commitizen地址改为本地安装下的cz-conventional-changelog
    "commitizen": {
      "path": "node_modules/cz-conventional-changelog"
    }
  },
  "repository": {
    "type": "git",
    "url": "git+https://github.com/wuhaohao1234/learncommitizen-.git"
  },
  "keywords": [],//关键字
  "author": "wuhaohao <1611499758@qq.com>",
  "license": "ISC",
  "bugs": {
    "url": "https://github.com/wuhaohao1234/learncommitizen-/issues"
  },
  "homepage": "https://github.com/wuhaohao1234/learncommitizen-#readme",
  "devDependencies": {  //项目依赖
    "commitizen": "^3.0.5",
    "cz-conventional-changelog": "^2.1.0"
  }
}

```

4. 向缓存中提交修改

git status

git add .

git cz(这里会让你选择commit的类型,以及一大堆东西)

git push

## 4、参考链接

[知乎](https://zhuanlan.zhihu.com/p/34223150)

[阮一峰的commit](http://www.ruanyifeng.com/blog/2016/01/commit_message_change_log.html)