+ Wikipedia：[PyQt](https://en.wikipedia.org/wiki/PyQt)
+ 官方文档：[PyQt Documentation](https://www.riverbankcomputing.com/static/Docs/PyQt6/installation.html#understanding-the-correct-version-to-install)

PyQt是跨平台的UI工具Qt的Python接口，用于UI设计，最新版本为PyQt6，版本之间差异不大

```bash
pip  install  pyqt6
```

（Qt原版使用C++，其他Python接口还包括PySide）

---
## 参考资料

+ 文档
	+ Qt 原版模块（C++）：[Qt Modules](https://doc.qt.io/qt.html)
	+ PyQt6 模块：[PyQt6 Modules](https://www.riverbankcomputing.com/static/Docs/PyQt6/module_index.html#ref-module-index)
	+ Tutorials Point教程：[PyQt Tutorial](https://www.tutorialspoint.com/pyqt/pyqt_basic_widgets.htm)

+ 视频课程
	+ SilverFox的课程：[Pyqt5 Qt Designer简约风格界面设计](https://space.bilibili.com/9989/channel/collectiondetail?sid=758621)
	+ Udemy课程：[使用 PyQt6 和 Qt 设计器进行 Python GUI 开发](https://www.bilibili.com/video/BV1US4y1P7ae?p=1&vd_source=d208713af4296ed6230d640d411a0ebf)
	+ Tech with Tim Designer教程：[PyQt5 Python 3 Tutorial](https://www.youtube.com/playlist?list=PLzMcBGfZo4-lB8MZfHPLTEHO9zJDDLpYj)

---
## 学习笔记

+ 风格设计 - 控件的美术风格设置
	+ [[尺寸和位置 Size & Position]]
	+ [[留空与间隔 Spacing & Margin]]
	+ [[样式表 Style Sheet]]
+ 控件 - UI设计的基本元素
	+ 布局设计控件 - 控件间的排列和从属关系
		+ [[布局 Layout]]
		+ [[空位 Spacer]]
		+ [[容器 Container]]
	+ 程序与窗口控件 - Qt程序运行的基础
	+ 输入控件 - 等待用户的动作
		+ [[按钮 Buttons]]
	+ 显示控件 - 输出反馈

---
## 常用模块 Modules

+ PyQt6 Modules：[PyQt6 Modules](https://www.riverbankcomputing.com/static/Docs/PyQt6/module_index.html#ref-module-index)

PyQt库有很多不同功能的模块，甚至有支持传感器、蓝牙、串口、内购的模块，但一般用不到这么复杂的功能，常用的有：

+ `QtWidgets` - 创建经典UI控件，大部分都是`QWidget`的子类
+ `QtGUI` - 用于创建图片、视频、字体等设计要素的类，一般由`QtWidgets`调用

模块内部控件工具的导入：

```python
from PyQt6.QtWidgets import QApplication, QMainWindow, QLabel, QPushButton
from PyQt6.QtGui import QIcon, QAction
```

---



