+ 文档：[Layout Management](https://doc.qt.io/qt-6/layout.html)

布局工具用于设置控件在容器中的摆放位置和排列顺序，并自动适应窗口的缩放大小

容器的`setLayout()`函数可以将布局对象与容器关联

---
## 水平布局和垂直布局 Horizontal and Verticle Layout

这两种布局对应的类分别为`QHBoxLayout`和`QVBoxLayout`，会按添加的顺序将控件依次水平或竖直排列在容器内部

以水平排列为例，首先创建一个布局对象并关联到容器`widget`

```python
widget = QWidget()
layout = QHBoxLayout()
widget.setLayout(layout)
```

创建的一系列控件依次添加到布局中

```python
button_1 = QButton()
layout.addWidget(button_1)

label_1 = QLabel("Example")
layout.addWidget(label_1)
```

---
## 栅格布局 Grid Layout



---
## 表格布局 Form Layout



---
## 问题记录 - 主窗口设置布局报错

设置主窗口的整体布局`main_layout`时，如果直接调用主窗口的成员函数`setLayout()`会报错“主窗口已经有布局”，原因未知

+ 解决方案：先设置一个“中心控件”`central_widget`，将控件添加到中心控件关联的布局中

```python
class MainWindow(QMainWindow):
    def __init__(self):
        super().__init__()
        
        central_widget = QWidget()
        self.setCentralWidget(central_widget)
        self.main_layout = QVBoxLayout(central_widget)
```
