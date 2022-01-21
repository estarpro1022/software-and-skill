## Github使用指南

***

#### GitHub加速方法

1. 加速方法，将GitHub仓库地址克隆下来，在码云gitee上导入，然后在git clone

2. 完成之后，再 .git 文件夹的config中修改remote origin 中gitee 为 github

#### 寻找开源项目

***

* 在搜索框进行筛选

```c
# 按照项目名/仓库名搜索（大小写不敏感）
in:name xxx
# 按照README搜索（大小写不敏感）
in:readme xxx
# 按照description搜索（大小写不敏感）
in:description xxx
# stars数大于xxx
stars:>xxx
# forks数大于xxx
forks:>xxx
# 编程语言为xxx
language:xxx
# 最新更新时间晚于YYYY-MM-DD
pushed:>YYYY-MM-DD
```

#### 远程仓库

***

##### 添加远程仓库

* git remote add origin`<url>`  添加远程仓库
  * fatal: remote origin already exists. 说明已添加远程设备
  * git remote -v       查看远程URL

##### 修改远程仓库

* git remote set-url origin `<url>`

##### 重命名远程仓库

git remote rename 

两个参数：

* 现有的远程名称，如`origin`
* 要改成的名称， 如  `destination`

`git remote rename origin destination`

##### 删除远程仓库

git remote rm `<name>`

#### 分支

***

* 创建新的分支并推送到github
  * git checkout -b `branch-name`
  * git push origin `branch-name`
  * 貌似还有一种方法:
    * git push origin HEAD -u //将创建分支的信息推送给github
* 删除github远程分支
  * git push origin :`branch-name`

#### Fork

疑问：fork，将本地分支与原始仓库同步，用github fetch upstream融合，本地的会改变吗

* 应该不会，要git pull更新本地仓库