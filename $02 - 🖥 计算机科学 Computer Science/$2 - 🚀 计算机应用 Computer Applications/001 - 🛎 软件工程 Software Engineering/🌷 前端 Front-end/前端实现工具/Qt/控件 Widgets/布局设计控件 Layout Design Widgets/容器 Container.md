容器是一类特殊的控件，其内部可以包含其他控件，通常UI窗口中的子区域就是由不同的容器组成。在一个PyQt程序中，容器的包含关系形成树状结构，最大的容器就是主窗口`QMainWindow`

往容器中放置控件需要调用其所使用的布局对象的`addWidget()`函数。

+ [[#控件容器 Widget]]
+ [[#工具栏 Toolbar]]
+ [[#菜单栏 Menubar]]
+ [[#分组框 Group Box]]
+ [[#滚动区域 Scroll Area]]

---
## 控件容器 Widget

`QWidget`既是控件的父类，本身也可以作为一种基本容器使用，注意`QWidget`本体默认在窗口中不可见

```python
widget = QWidget()
layout = QHBoxLayout()
widget.setLayout(layout)
```


---
## 工具栏 Toolbar

工具栏指的是主窗口上方的一排按钮，使用`QMainWindow`类的`addToolBar()`函数创建，通过`QMainWindow`的`addToolBar()`函数可以添加按钮

作为从属于主窗口的特殊容器，工具栏不需要指定布局

```python
class MainWindow(QMainWindow):
    def __init__(self):
        super().__init__()
        
		self.toolbar = self.addToolBar("Toolbar")
		
		save_action = QAction("Save", self)
		self.toolbar.addAction(save_action)
		
		load_action = QAction("Load", self)
		self.toolbar.addAction(load_action)
		
		add_event_action = QAction("Add Event", self)
		self.toolbar.addAction(add_event_action)
```

用`setStyleSheet()`修改设计风格

```python
        self.toolbar.setStyleSheet("""QToolBar {
                                        background-color: #F5FFFA;
                                        border: 1px solid #ccc;
                                        padding: 5px;
                                      }

                                      QToolBar QToolButton:hover {
                                        background-color: #97f2f0;
                                        }

                                      QToolBar QToolButton:pressed {
                                        background-color: #4CAF50;
                                        }
                                   """)
```


---
## 菜单栏 Menubar


---
## 分组框 Group Box

分组框是一种可以切换状态的容器，当其状态设置为禁用`disabled`时，其内部所有子控件都不能操作


---
## 滚动区域 Scroll Area

创建一个子控件`QWidget`，将其置入滚动区域`QScrollArea`，若子控件不能完整显示，就会出现滚动条。一个滚动区域只能有一个子控件，用`setWidget()`重新设置会覆盖旧的子控件

```python
widget = QWidget()
layout = QGridLayout()
widget.setLayout(layout)

scroll = QScrollArea()
scroll.setWidget(self.task_list_widget)
```

---
## 