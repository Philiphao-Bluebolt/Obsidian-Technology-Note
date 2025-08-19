+ **参考** - [文档](https://openpyxl.readthedocs.io/en/stable/index.html)

Openpyxl是一个轻量的Excel读写控制库，可以先编辑后保存，仅支持`.xlsx`格式

```python
from openpyxl import Workbook, load_workbook
from openpyxl import PatternFill, Font, Color, PatternFill, Border, Side
```

+ [工作簿与工作表](#工作簿与工作表)
+ [单元格操作](#单元格操作)

---
## 文档目录

官方文档维护不当，缺失目录，这里是我手写的目录

+ [Tutorial](https://openpyxl.readthedocs.io/en/stable/tutorial.html) - 安装
+ [Simple Usage](https://openpyxl.readthedocs.io/en/stable/usage.html) - 工作表基本使用
+ [Working with Styles](https://openpyxl.readthedocs.io/en/stable/styles.html) - 样式设置
+ [Working with Rich Text](https://openpyxl.readthedocs.io/en/stable/rich_text.html) - 富文本（部分字符）样式
+ [Conditional Formatting](https://openpyxl.readthedocs.io/en/stable/formatting.html) - 条件格式
+ [Inserting and Deleting Rows and Columns, Moving Ranges of Cells](https://openpyxl.readthedocs.io/en/stable/editing_worksheets.html)
[Additional Worksheet Properties](https://openpyxl.readthedocs.io/en/stable/worksheet_properties.html)
[Validating Cells](https://openpyxl.readthedocs.io/en/stable/validation.html)
[Worksheet Tables](https://openpyxl.readthedocs.io/en/stable/worksheet_tables.html)
https://openpyxl.readthedocs.io/en/stable/filters.html
https://openpyxl.readthedocs.io/en/stable/print_settings.html
https://openpyxl.readthedocs.io/en/stable/pivot.html
https://openpyxl.readthedocs.io/en/stable/comments.html
https://openpyxl.readthedocs.io/en/stable/datetime.html
https://openpyxl.readthedocs.io/en/stable/simple_formulae.html
https://openpyxl.readthedocs.io/en/stable/defined_names.html
https://openpyxl.readthedocs.io/en/stable/workbook_custom_doc_props.html
https://openpyxl.readthedocs.io/en/stable/protection.html
https://openpyxl.readthedocs.io/en/stable/charts/introduction.html
https://openpyxl.readthedocs.io/en/stable/charts/area.html
https://openpyxl.readthedocs.io/en/stable/charts/bar.html
https://openpyxl.readthedocs.io/en/stable/charts/bubble.html
https://openpyxl.readthedocs.io/en/stable/charts/line.html
https://openpyxl.readthedocs.io/en/stable/charts/scatter.html
https://openpyxl.readthedocs.io/en/stable/charts/pie.html
https://openpyxl.readthedocs.io/en/stable/charts/doughnut.html
https://openpyxl.readthedocs.io/en/stable/charts/radar.html
https://openpyxl.readthedocs.io/en/stable/charts/stock.html
https://openpyxl.readthedocs.io/en/stable/charts/surface.html
https://openpyxl.readthedocs.io/en/stable/charts/limits_and_scaling.html
https://openpyxl.readthedocs.io/en/stable/charts/secondary.html
https://openpyxl.readthedocs.io/en/stable/charts/chart_layout.html
https://openpyxl.readthedocs.io/en/stable/charts/pattern.html
https://openpyxl.readthedocs.io/en/stable/charts/gauge.html
https://openpyxl.readthedocs.io/en/stable/charts/chartsheet.html
https://openpyxl.readthedocs.io/en/stable/charts/anchors.html
https://openpyxl.readthedocs.io/en/stable/charts/graphical.html
https://openpyxl.readthedocs.io/en/stable/images.html
https://openpyxl.readthedocs.io/en/stable/pandas.html
https://openpyxl.readthedocs.io/en/stable/optimized.html
https://openpyxl.readthedocs.io/en/stable/performance.html
https://openpyxl.readthedocs.io/en/stable/development.html

---
## 工作簿

**工作簿 Workbook**（`wb`）是一个等同于完整Excel文件的**对象**，可以新建也可以从已有的`.xlsx`文件加载。所有对工作簿进行的修改保存在内存中，必须使用`wb.save`才会保存到文件。

```python
from openpyxl import Workbook, load_workbook

# 新建
wb = openpyxl.Workbook()

# 从已有文件加载
wb = openpyxl.load_workbook("./my_excel_file.xlsx")

# 保存
wb.save("./my_excel_file.xlsx")
```

---
## 工作表

**工作表 Worksheet**（`ws`）是工作簿里的一份**表格**，每个新建的工作簿都默认有一份工作表。

```python
from openpyxl import Workbook, load_workbook

# 创建并指定位置：
ws1 = wb.create_sheet("Sheet 1") # 默认最后
ws2 = wb.create_sheet("Sheet 2", 0) # 第一
ws2 = wb.create_sheet("Sheet 2", -1) # 倒数第二
```


---
## 行与列 

访问行与列的操作多用于设置行高和列宽，访问时输入的编号格式与原版Excel一致，行用数字表示，列用字母表示

+ **访问行**：`ws.row_dimensions[4]` - 数字编号
+ **访问列**：`ws.column_dimensions['AC']` - 字母编号
+ **数字转字母**：`openpyxl.utils.get_column_letter('34')`

```python
from openpyxl.utils import get_column_letter

ws.row_dimensions[4].height = 20
ws.column_dimensions["AH"].width = 19
ws.column_dimensions[get_column_letter(34)].width = 19
```


---
## 单元格选取








---
## 样式设计