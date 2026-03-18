+ QtWidgets：[QtWidgets](https://www.riverbankcomputing.com/static/Docs/PyQt6/api/qtwidgets/qtwidgets-module.html)

+ [[#初始化应用 Initialization Application]]
	+ [[#主窗口`MainWindow`]]


---
## 初始化应用 Initialization Application

PyQt需要`QApplication`模块进行初始化并创建窗口，窗口由继承`QMainWindow`的自定义对象`MainWindow`驱动

```python
### Program Entrance
def main():
    app = QApplication(sys.argv) 
    window = MainWindow() 
    window.show()
    sys.exit(app.exec())

if __name__ == "__main__":
    main()
```

### 主窗口`MainWindow`

这是定义主窗口布局的类，继承自`QMainWindow`

```python
class MainWindow(QMainWindow):
    def __init__(self):
        super().__init__()
        pass
```

---
