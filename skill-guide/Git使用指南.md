### Git使用指南

git自动帮你配path路径





下载的太慢可以找镜像网站

![image-20220118230952172](C:\Users\estar\AppData\Roaming\Typora\typora-user-images\image-20220118230952172.png)

git config user.name/user.email 可查看姓名和邮箱

git config -l : 查看配置列表

git config --system -l: 查看系统配置
git config --global --list ：自己配的

c/user/estar/.gitconfig查看全局配置

卸载：反安装，清理环境变量

ctrl+鼠标滚轮放大缩小界面

**环境变量只是为了全局使用而已**

##### linux风格的基本操作

cd ..进入上一级目录

cd dir 进入当前目录的下一级目录

clear 清屏(真的全部清空了)

ls 显示文件情况

ll  显示的更详细

touch 创建文件

rm 删除文件

mkdir 创建目录

rm -r  删除目录

mv  移动文件 

> mv index.html(文件) test(目录)

reset 重新初始化终端——相当于重新打开终端

history 查看历史命令

井号 # 表示注释

exit 退出

#### 想要获取帮助：

* git <verb> --help(较为详细)

> git config --help

* git <verb> -h (可用选项的快速参考)

> git add -h

#### git 理论核心：

三个区域：工作目录(working directory)，暂存区(stage/index)，资源库(repository / Git repository)

工作区：存放代码的区

暂存区：是个文件

仓库：有提交代码的数据

git add 

git commit

git push

![image-20220119171455006](C:\Users\estar\AppData\Roaming\Typora\typora-user-images\image-20220119171455006.png)

#### 建立一个git仓库

##### 在已存在目录中初始化仓库

1. cd /d/code/my_project
2. git init(initialize)

如果在一个有文件的文件夹中，

```bash
$ git add *.c
$ git add LICENSE
$ git commit -m 'initial project version'
```

##### 克隆现有的仓库

git clone <url> new_name(自定义仓库名字)

> new_name选填

git status : 查看当前文件状态

echo 'hello' > readme  ——创建了一个readme文件，虽然格式未知

不推荐上述创建文件的做法

git add README // 开始追踪该文件

>  git add 可以用它开始跟踪新文件，或者把已跟踪的文件放到暂存区，还能用于合并时把有冲突的文件标记为已解决状态

git add .

git add -A   这两个指令将当前文件夹所有文件纳入跟踪

git add `文件夹` 可以直接添加文件夹

![image-20220120224045104](C:\Users\estar\AppData\Roaming\Typora\typora-user-images\image-20220120224045104.png)

git status -s 精简版输出文件状态

新添加的未跟踪文件前面有 `??` 标记，

新添加到暂存区中的文件前面有 `A` 标记，

修改过的文件前面有 `M`标记。

`M` 有两个可以出现的位置，出现在右边的 `M` 表示该文件被修改了但是还没放入暂存区，出现在靠左边的 `M` 表示该文件被修改了并放入了暂存区。`MM`文件的修改中既有已暂存的部分，又有未暂存的部分

##### 忽略文件

<img src="C:\Users\estar\AppData\Roaming\Typora\typora-user-images\image-20220119173811822.png" alt="image-20220119173811822" style="zoom:200%;" />

![image-20220120223828606](C:\Users\estar\AppData\Roaming\Typora\typora-user-images\image-20220120223828606.png)

cat .gitignore

.idea/ 忽略.idea所有东西

*.[oa]

*~

查看已暂存和未暂存的修改

git diff  查看尚未暂存的文件更新了哪些部分，即当前文件和暂存区域快照之间的差异

git diff --staged 查看已暂存的与最后一次提交的文件差异

***

每次准备提交前，先用 `git status` 看下

git commit: 进入编辑页面

git commit -m "message"

提交时记录的是放在暂存区域的快照。 任何还未暂存文件的仍然保持已修改状态，

![image-20220121130026831](C:\Users\estar\AppData\Roaming\Typora\typora-user-images\image-20220121130026831.png)

##### 跳过使用暂存区域

git commit -a -m "message"

##### 移除文件

git rm <doc> 		和git rm -f 区别是什么

删除目录 git rm <dir> -r -f

##### 撤销文件

> git reset HEAD^ doc

git rm --cached (-r) doc(folder)

回退文件至上一版本

##### 提交至远程仓库

git push出错的解决方法

![image-20220120231234757](C:\Users\estar\AppData\Roaming\Typora\typora-user-images\image-20220120231234757.png)

##### 记录文件日志

git log

> :q退出

##### 版本切换

git checkout fe923(40位只需要输入5位)

master对应的是最新一次的提交，而fe923是某次具体的提交

#### 分支

* git branch 查看分支
* git branch -r  查看远程分支
* git branch -a 查看所有分支
* git branch [branch-name] 新建分支，但仍停留在当前分支
* git merge [branch] 合并指定分支到当前分支
* git checkout -b [branch-name] 新建分支，并切换到该分支
* git branch -d [branch-name] 删除分支
  * 不能删除当前分支，要先git checkout


主分支需要稳定，一般不允许在上面工作，可以在新建的dev分支上工作，工作完后再合并到主分支上

* 解决master 和 main不同提交历史导致无法pull request的问题

![image-20220121132141770](C:\Users\estar\AppData\Roaming\Typora\typora-user-images\image-20220121132141770.png)

这是创建了新的main分支吗

master和main分支始终同步







团队很重要

#### 问题：

##### .gitignore /前后区别，如何忽略目录下全部内容，目录下的某个文件或目录

git , clion, GitHub联动

github main分支