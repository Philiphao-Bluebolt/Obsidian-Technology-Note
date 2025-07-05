这是PyQt附带的图形化设计器，需要下载另一个库

```bash
pip  install  pyqt6-tools
```

程序名称为"designer.exe"，可执行文件藏在虚拟空间的PyQt库文件夹中，找不到就用搜索功能查找

![[Pasted image 20240702203650.png]]

---
## 格式转换 .ui --> .py

Qt Designer保存的文件类型为.ui，可以使用命令行工具`pyuic6`转换为.py文件：

```bash
pyuic6  -x  design_layout.ui  -o  design_code.py 
```

.ui实际上基于XML文件

---
## Python直接导入.ui文件

可以在代码直接用`uic`模块的`loadUi()`函数导入.ui文件

```python
class UI(QMainWindow):
    def __init__(self):
        super().__init__()
        
        uic.loadUi("../main_window.ui", self)
```

注意这里定义的类`UI`的继承类（`QMainWindow`）必须和Qt Designer中创建类型一致，比如说，Qt Designer创建了MainWindow类型，使用时就要导入到`QMainWindow`类（导入到`QWidget`类会报错）

