这部分函数用于精确定义控件的位置（相对于其父控件）和尺寸，参数单位是像素px；注意这些设置和布局是冲突的

+ 设置控件的位置（XY）和尺寸（宽高）

```python
widget.setGeometry(100, 100, 400, 200)
```

+ 固定控件的尺寸使其不受窗口缩放影响

```python
widget.setFixedWidth(400)
widget.setFixedHeight(200)
widget.setFixedSize(400, 200)
