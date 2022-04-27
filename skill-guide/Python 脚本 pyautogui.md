## Python 脚本 pyautogui

主要功能是实现键盘和鼠标的自动操作，这里介绍一些常用函数

首先安装pyautogui，命令行输入`python -m pip install -U pyautogui` ，可以把其依赖的包给下载了。

### 基本函数

```python
pyautogui.PAUSE = 1
pyautogui.FAILSAFE = True
pyautogui.size()
pyautogui.Point(x, y)
```



```python
import pyautogui

pyautogui.PAUSE = 1 # 执行pyautogui函数后停顿，不过还没有发现有这个功能，不如用time.sleep(1)
pyautogui.FAILSAFE = True	# 防故障功能。执行脚本时，如果将鼠标移至左上方，就会报错，从而停止执行。

width, height = pyautogui.size()	# 获取屏幕大小 (position_x, position_y)

pyautogui.Poine(100, 100) # 产生Point类型的二元元组
```

pyautogui的x轴水平向右，y轴竖直向下，同easyx



### 鼠标操作

```python
pyautogui.position()
pyautogui.moveTo()
pyautogui.moveRel()
pyautogui.click()
pyautogui.dragTo()
pyautogui.mouseDown()
pyautogui.mouseUp()
```



```python
import pyautogui

# positon()获取鼠标位置，返回二元元组
positon = pyautogui.position()
position_x, position_y = pyautogui.position()

# moveTo()，参数可以为x, y，也可以是元组(x, y)，列表[x, y]
pyautogui.moveTo(x, y)	# 移动至(x, y)
pyautogui.moveTo(position)				# 花零秒时间移动
pyautogui.moveTo(position, duration=1)	# 花一秒时间移动

# moveRel() 参数同上，表示相对位移
pyautogui.moveRel(100, -100) # 向右移动100， 向上移动100

# click()
pyautogui.click() #点击当前位置，也可以传入位置
pyautogui.click(100, 100, button='left', duration=1)	# 花一秒移动到(100,100) ，左键点击

# dragTo()
pyautogui.dragTo(position, duration=1)	# 花一秒按下鼠标移动到(100,100)

# mouseDown()	# 鼠标按下
# mouseUp()
mouseDown()
moveTo(100, 100, duration=1)
mouseUp()
# 等效于
dragTo(100, 100, duration=1)
```



### 键盘操作

```python
# pyautogui.KEYBOARD_KEYS 所有支持的按键
pyautogui.typewrite()
pyautogui.press()
pyautogui.hotkey()
```

```python
import pyperclip
# typewrite，一次多个字母
pyautogui.typewrite('a', 'b', 'c')
pyautogui.typewrite(['a', 'b', 'c', 'shift'], interval=0.5)# 推荐放在列表里，并且shift能转义
# interval 指输入间隔
pyautogui.typewrite('a', 'b', 'c', 'shift')	# WRONG!!!

# press()，模拟键盘按键，一次一个键
pyautogui.press('shift')

# hotkey() 组合键
pyperclip.copy("你好")
pyautogui.hotkey('ctrl', 'v')
pyautogui.press('enter')
```

