### 打开方式

* Visual Studio Installer中启动

* 创建新项目

  ![image-20220128182226853](https://gitee.com/starriverflow/cloud-pictures/raw/master/img/image-20220128182226853.png)

* #### 选择C++，所有平台，桌面，点击Windows桌面应用程序

![image-20220128182317669](https://gitee.com/starriverflow/cloud-pictures/raw/master/img/image-20220128182317669.png)![image-20220128182432547](https://gitee.com/starriverflow/cloud-pictures/raw/master/img/image-20220128182432547.png)![image-20220128182619077](https://gitee.com/starriverflow/cloud-pictures/raw/master/img/image-20220128182619077.png)![image-20220128182638502](https://gitee.com/starriverflow/cloud-pictures/raw/master/img/image-20220128182638502.png)



* #### 注意修改后缀

![image-20220128183329964](https://gitee.com/starriverflow/cloud-pictures/raw/master/img/image-20220128183329964.png)



* #### 工具 -- 选项 -- 环境 -- 字体和颜色，调整为Consolas字体（等宽字体）

* #### 行号

![image-20220128190511998](https://gitee.com/starriverflow/cloud-pictures/raw/master/img/image-20220128190511998.png)

### 一些常见错误

#### 拒绝访问式错误

* 可能放在C盘敏感位置——需要管理员权限，可以用管理员身份打开VS
* 杀毒软件
* **执行了两次**，新的窗口取代了旧的窗口，但是有的代码不能这样。
* 代码自身问题

#### 错误处理

双击错误，可跳到错误地点

### 快捷键

| 快捷键                          | 含义                     |
| ------------------------------- | ------------------------ |
| ctrl + shift + /                | 注释                     |
| ctrl + x                        | 删除                     |
| ctrl + c                        | 光标置于某一行，复制整行 |
| Tab                             | 缩进、自动扩展           |
| ctrl + a, 然后按住ctrl 按下 k f | 自动对齐                 |
|                                 |                          |

ctrl + shift + / ：注释

ctrl + x 删除

### 注意事项：

#### 创建多个源文件

如果一个项目有两个源文件，那就只能有一个main，另一个要改成main_`number`，此时点击执行，执行的是main函数所在的文件。

#### 写一段文件就自动保存

ctrl + s



* .sln后缀的文件就是项目工程文件，.c后缀的只能编辑

* release版本，将x64文件夹中的.exe文件发给别人，可以直接打开

* debug版本，x64文件夹中的.exe别人如果未安装.exe不能打开（但是我这没有.exe文件）

  后来又有了，**生成解决方案**就可以

* release版本的文件比debug**小六倍**

![image-20220128203216520](https://gitee.com/starriverflow/cloud-pictures/raw/master/img/image-20220128203216520.png)

![image-20220128203657229](https://gitee.com/starriverflow/cloud-pictures/raw/master/img/image-20220128203657229.png)



x86一般是32位电脑用的

x64向下兼容x86



#### 推荐书籍

* C Primer Plus
* 谭浩强的红皮书==不推荐==

