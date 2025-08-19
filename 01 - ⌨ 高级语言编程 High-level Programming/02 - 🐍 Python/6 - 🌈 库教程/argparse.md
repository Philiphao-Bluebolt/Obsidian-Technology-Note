argparse是一个参数解析标准库，它可以定义、读取Python命令后缀参数


---
## 基础用法

下面这段代码定义并读取了两个命令行参数，`--year`和`--month`，两个参数在执行Python脚本时都是必须输入的（`required=True`）

```python
import argparse

# 创建
parser = argparse.ArgumentParser(description='Year and month input')
parser.add_argument("--year", type=int, required=True)
parser.add_argument("--month", required=True)
args = parser.parse_args()

print(args.month)
print(args.year)
```

执行命令的参数格式

```bash
python calender.py --year 2025 --month 08
```