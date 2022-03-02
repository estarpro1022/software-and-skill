### 颜色

红绿蓝三原色

RGB(5, 5, 5)

red green blue

### 坐标轴

* EasyX左上角为坐标原点，向右x轴正方向，向下y轴正方向

​		度量单位像素点

* 设备



设备分两种：

* 默认绘图窗口
* IMAGE对象。SetWorkingImage()函数可以设置当前绘图的设备

默认绘图窗口编号为0

举例：

两张纸，编号1和2，SetWorkingImage(1)，在1上作图



### 窗口函数

* initgraph(int width, int height, int flag = NULL); 初始化绘图窗口(创建窗口)

  一般initgraph(640, 480);

  NOMINIMIZE: 不能最小化

  NOCLOSE: 关不掉

  SHOWCONSOLE: 展示控制台

  或运算将多个flag连接

* closegraph(); 关闭绘图窗口

* cleardevice(); 清空绘图设备



### 绘制各种图形

* 填充样式分为无填充、有边框填充、无边框填充

以画圆为例

circle();

fillcircle();

solidcircle();

* 形状

circle ellipse pie rectangle roundrect line

* 填充颜色 setfillcolor(YELLOW);

* 设置线条颜色 setlinecolor(BLUE);
* 设置线条样式 setlinestyle();

setlinestyle(PS_SOLID, 5);     实线，宽度5像素。可以跳到定义

==也可以ctrl + 左击==



![image-20220217194026363](https://gitee.com/starriverflow/cloud-pictures/raw/master/img/image-20220217194026363.png)

![image-20220217194058488](https://gitee.com/starriverflow/cloud-pictures/raw/master/img/image-20220217194058488.png)



PS_SOLID: 实线

PS_DASH: 虚线

大部分设置都是set



### 设置背景颜色，两步才能设置背景颜色

setbkcolor(WHITE);

cleardevice();  // 用当前背景色——白色填充设备，并将当前坐标移至(0, 0)



### 文字绘制函数，用于在窗口上绘制文字

settextcolor(RED);  // 设置字体颜色

outtextxy(int x, int y, LPCTSTR str);  在指定位置输出字符串，字体默认白色，只能输入一个字符

当传入"hello"报错，是由于字符集导致的

##### 解决方案

* 在字符串双引号前面加上大写的L
* 用TEXT()把字符串包起来，TEXT("hello");
* _T()，原理同上



#### 设置文字样式

settextcolor(RED);

settextstyle(int hight, int width, L"楷体");

<u>width为0表示自适应</u>

<u>设置文字背景模式，TRANSPARENT</u>

设置完字体就设置背景模式

setbkmode(TRANSPARENT)

```c++
settextcolor(RED);
settextstyle(50, 0, "楷体");
setbkmode(TRANSPARENT)
```

采集颜色：

QQ截图，按c



textheight(str);  获取字符串实际占用的像素高度

textwidth(str);   获取字符串实际占用的像素宽度



设置矩形：

fillrectangle(100, 100, 300, 300);

左上坐标和右下坐标

```c++

settextcolor(RGB(173, 0, 13));
setfillcolor(YELLOW);
fillrectangle(100, 100, 300, 300);
outtextxy(230, 150, L"hello");
```

如何居中显示？

```c++
fillrectangle(100, 100, 300, 300);
wchar_t arr[] = L"hello";
// 这样outtextxy才不会报错，用char类型会报错
int width = textwidth(arr);
int height = textheight(arr);

outtextxy(200 - width / 2, 200 - height / 2, arr);
```



### 图像处理函数

* 定义一个变量

```c++
IMAGE img;
```

* loadimage, 从文件中读取图像, png格式不支持透明
  * pDstlmg 保存图像的image对象指针
  * plmgFile 文件名， 图片保存在与cpp同目录下
  * nWidth  图片拉伸宽度
  * nHeight 图片拉伸高度
  * bResize = false 是否调整image的大小以适应图片
* putimage 当前设备上绘制指定图像
  * dstX 左上角x
  * dstY 左上角y
  * pSrcImg 要绘制的对象指针
  * dwRop = SRCCOPY 三元光栅操作码



```c++
// 输出图片
IMAGE img;	// 定义一个对象(变量)
// 加载图片
// 相对路径：./表示当前文件夹下，../表示当前文件夹的父目录
// 绝对路径：C:\\...\\...需要两个反斜杠，转义，有空格\'he llo\''
loadimage(&img, "", 250, 250);
putimage(0, 0, &image);
```



### 鼠标操作

* 使用MOUSEMSG类型

```c++
MOUSEMSG msg;
```

* 用MouseiHit() 判断是否有鼠标消息(左键、右键、中间、移动)
* 有鼠标消息就能接收鼠标消息了，msg = **GetMouseMsg()**;

* 鼠标消息成员

  * uMsg: 当前鼠标消息

    uMsg的两个主要消息

    * WM_LBUTTONDOWN 鼠标左键消息
    * WM_RBUTTONDOWN 鼠标右键消息

  * x:         当前鼠标x坐标

  * y:         当前鼠标y坐标

``` 
while(1) {
if (MouseHit()) {
// cleardevice();
    MOUSEMSg msg = GetMouseMsg();
    // 消息分发
    switch (msg.uMsg) {
        case WM_LBUTTONDOWN:
        	printf("%d, %d\n", msg.x, msg.y);
            outtextxy(400, 400, L"鼠标左键按下");
            break;
        case WM_RBUTTONDOWN:
            outtextxy(400, 400, L"鼠标右键按下:");
            break;
        default:
            break;
    }
}
}
```

判断鼠标是否点击某一个框

if (msg.x < 370 && msg.x > 270 && msg.y < 160 && msg.y > 120) {
					printf("This is the future\n");
}



### 新版鼠标操作

```c++
ExMessage msg;
if (peekmesssage(&msg, EM_MOUSE)) {
    switch (msg.message) {
        case WM_LBUTTONDOWN:
            if (msg.x >= && msg.x <= && msg.y <= && msg.y >=) {
                printf("hello");
            }
    }
}
```



### 非easyx函数——键盘消息

### 物体移动

* 获取键盘消息
  * getch();	#include <conio.h>
  * GetAsyncKeyState(键值)



```c++
while(1) {
    cleardevice();	// 把所有东西清除了，如果没有clear，圆的移动会有尾巴\
    // clear下方再定义img
    setfillcolor(BROWN);
    fillcircle(x, y, 20);
    char key = _getch();
    switch (key) {
        case 72: // 上键
        case 'w':
        case 'W':
            y -= 5;
            printf("上键\n");
            break;
        case 80: // 下键
        case 's':
        case 'S':
            y += 5;
            break;
        case 75: // 左键
        case 'a':
        case 'A':
            x -= 5;
            break;
        case 77: // 右键
        case 'd':
        case 'D':
            x += 5;
            break;
    }
}
```



### easyx其他函数

设备上进行cleardevice()，会出现闪屏现象，因此需要两个函数

* BeginBatchDraw();	// 开始批量绘图
* ---绘图代码---
* EndBatchDraw();      // 结束批量绘图，并执行未完成的绘制任务

双缓冲绘图，需要放在绘图代码前和后

getch不能斜向移动

```c++
BeginBatchDraw();
while (1) {
    fillcircle();
    FlushBatchDraw();
}
EndBatchDraw();
```

也可以(不推荐，有时还是会闪屏)

```c++
while (1) {
    BeginBatchDraw();
    fillcircle();
    EndBatchDraw();
}
```



### 键盘操作

if (kbhit()) 键盘是否输入字符

char key = getchar();

```c++
if (GetAsyncKeyState(VK_UP)) {
    y -= 5;
}
if (GetAsyncKeyState(VK_DOWN)) {
    y += 5;
}
if (GetAsyncKeyState(VK_LEFT)) {
    x -= 5;
}
if (GetAsyncKeyState(VK_RIGHT)) {
    x += 5;
}
```



### WindowsAPI播放音乐

* 包含头文件windows.h, mmsystem.h(包含graphics.h就不需要了)
  * 先加载graphics.h再放mmsystem.h（包含多媒体设备接口头文件）
* 加载静态库winmm.lib
* 使用mciSendString函数播放音乐

// 不能在循环里面

```c++
#include <stdio.h>
#include <graphics.h>
#include <conio.h>
#include <mmsystem.h>
#pragma comment(lib, "winmm.lib")	// 加载静态库，没有分号

void BGM() {
    // 打开音乐，播放音乐
    mciSendString("open ./ThatGirl.mp3", 0, 0, 0);	// 填0就好
    mciSendString("play ./ThatGirl.mp3", 0, 0, 0);
    // 取别名 alias
    mciSendString("open ./ThatGirl.mp3 alias BGM", 0, 0, 0);
    mciSendString("play BGM", 0, 0, 0);
    // 重复播放 repeat
    mciSendString("open ./ThatGirl.mp3 alias BGM", 0, 0, 0);
    mciSendString("play BGM repeat", 0, 0, 0);
    
    if (num == 0) {
        mciSendString("close BGM", 0, 0, 0);
    }
}
```



### 句柄

```c++
// 获取窗口句柄
HWND hnd = GetHWnd();
// 设置窗口标题
SetWindowText(hnd, "C语言Plus");
// 弹出窗口，提示用户操作
int isok = MessageBox(NULL, "hello world", "tips", MB_OKCANCEL);	// 返回值int
// MessageBox(hnd, "hello world", "tips", MB_OKCANCEL);	// 必须关闭才能操作easyx界面
if (isok == IDOK) {
    printf("你点击了OK");
    
} else if (IDCANCEL == isok) {
    printf("你点击了取消")
}
```











