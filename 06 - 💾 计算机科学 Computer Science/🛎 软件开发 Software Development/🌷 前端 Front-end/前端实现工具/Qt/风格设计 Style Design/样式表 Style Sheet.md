+ 格式：[The Style Sheet Syntax](https://doc.qt.io/qt-6/stylesheet-syntax.html)
+ 示例：[Qt Style Sheets Examples](https://doc.qt.io/qt-6/stylesheet-examples.html)

函数`setStyleSheet()`可以精细地定义控件的设计风格，如字体大小、背景颜色等，具体的输入格式参考官方文章

除了背景颜色`background-color`、字体大小`font-size`等公用的风格选项，每个控件都有一部分自己专用的风格选项，如按钮可以指定鼠标悬停、按下时的背景颜色

样式函数的输入格式范例如下：

```python
widget.setStyleSheet("""QToolBar {
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