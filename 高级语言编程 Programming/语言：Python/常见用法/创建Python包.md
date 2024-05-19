通过`pip`或者`conda`下载的库可以在任意位置调用，我们自己编写的模块只要包装成包也能实现任意位置调用

---
## __init__.py：包文件夹初始化

如果一个文件夹里含有一个`__init__.py`文件，代表这个文件夹是一个Python包（库），Python库的文件夹可以包含子文件夹，但是每一级文件夹都必须含有一个`__init__.py`文件

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

假设需要导入`plugin_1.py`文件里一个叫`Vector`的类，则需要

```python
from  my_package.plugins.plugin_1  import  Vector
```
