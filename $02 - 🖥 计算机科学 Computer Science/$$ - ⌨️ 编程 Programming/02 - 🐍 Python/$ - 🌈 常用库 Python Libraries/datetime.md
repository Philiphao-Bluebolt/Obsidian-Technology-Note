datetime是一个用于获取并处理日期的标准库

+ [基础用法](#基础用法)
+ [格式调整](#格式调整)

---
## 基础用法

> **获取当前日期** - 有两个库函数`now()`和`today()`可以用于获取现在的日期，其中`today()`只输出日期而不包含的当前时刻。

+ `datetime.datetime.now()` - 年、月、日、时、分、秒、微秒
+ `datetime.date.today()` - 年、月、日

```python


# Get current datetime
now = datetime.now()

# Get the date info
year = now.year # 2025
month = now.month # 8
day = now.day # 8
weekday_num = now.weekday() # 5
weekday_name = now.strftime('%A') # Friday
weekday_abbre = now.strftime('%a') # Fri

# Get the time info
current_time = now.time() # 12:35:06.131453
hour = now.hour # 13
minute = now.minute # 45 
second = now.second # 7
microsecond = now.microsecond # 132233
```


---
## 格式调整

> **星期** - 常用的星期格式有三种，分别是数字、英文全称和英文缩写

```python
from datetime import datetime

# 数字星期 5
weekday_num = now.weekday()

# 英文星期 Friday
weekday_name = now.strftime('%A')

# 英文缩写星期 Fri
weekday_abbre = now.strftime('%a')

```

> **时刻** - 