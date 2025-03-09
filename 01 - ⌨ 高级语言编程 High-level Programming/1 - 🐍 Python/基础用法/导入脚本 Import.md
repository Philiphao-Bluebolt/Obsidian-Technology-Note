Python脚本既可以作为主程序运行，也可以被其他脚本调用。若把编写的脚本封装成完整的文件夹并发布到PyPi等平台上，便成为一个库（Package）

导入脚本的关键词是`import`，类似C++的`<include>`

---
## 语句`import`

假设这里需要从`matplotlib`的子模块`pyplot`导入一个函数`plot()`，`import`的不同导入方法会影响函数的命名空间。

+ 导入整个库

```python
import  matplotlib

matplotlib.pyplot.plot() 
```

+ 导入所有子模块

```python
from  matplotlib  import  *

pyplot.plot()
```

+ 仅导入子模块且重命名（推荐）

```python
# 导入效果一样，选一个就行
import  matplotlib.pyplot  as  plt
from  matplotlib  import  pyplot  as  plt

plt.plot() 
```

+ 仅导入函数（不推荐，容易撞名）

```python
from  matplotlib.pyploy  import  plot

plot()
```

---
## 本地调用

一个合法的Python库文件夹里必须含有一个`__init__.py`文件，可以是空文件；Python库文件夹可以包含子文件夹，但是每一级文件夹都必须含有一个`__init__.py`文件。

+ `my_package`
	+ `__init__.py`
	+ `model.py`
	+ `test.py`
	+ `plot_result.py`
	+ `run.py`
	+ `plugins`
		+ `__init__.py`
		+ `plugin_1.py`
		+ ...

+ 指定导入：导入`plugin_1.py`文件里一个叫`Vector`的类

```python
from  my_package.plugins.plugin_1  import  Vector
```

+ 全部导入：导入`plugin_1.py`文件里所有函数和类

```python
from  my_package.plugins.plugin_1  import  *
``````

+ 导入同一个路径其他脚本

```python
from  .model.py  import  *
```

---
## 第三方库调用

Pip或者Conda的第三方库装好以后，直接按照官方教程`import`即可，不过一般模块的缩写有约定俗成的规则，比如说：

```python
from  matplotlib  import  pyplot  as  plt
import  numpy  as  np
import  tensorflow  as  tf
```

---
## 地狱笑话
 
```python
import  torch  as  tf
import  pandas  as  np
```