# Gitignore 研究

git status 

* 编译器.idea文件夹中.gitignore貌似和git的.gitignore不冲突

git add dir/

git add dir两者都可以

最好在末尾加个/



git status --ignored：**查看被忽略的文件**

cat .gitignore：**查看.gitignore**文件中的内容

*.txt 是忽略所有的txt文件，不管是当前目录还是子目录的txt文件

git rm -r --cached dir   不跟踪目录要加 -r（recursive）

忽略一整个文件夹

* read
* read/
  * 两者都可

忽略一个文件夹中的一个子文件夹

* read/listen/

忽略目录最好以/结尾

read目录有listen目录和listen.txt文件

ignore：

* read/listen 
  * 忽略listen 目录
* read/listen.txt
  * 忽略listen.txt文件



***

目前会这些就够了，我们已经掌握了如何忽略文件的主要方法







### 疑问：

* ignore的文件再git add 无效？
  * git add -f doc 强制添加

* 前面加/什么意思
  * ignore `/read`好像和read/效果相同
* /放在前面和后面的差别
* first-repository为什么pull request不成功
