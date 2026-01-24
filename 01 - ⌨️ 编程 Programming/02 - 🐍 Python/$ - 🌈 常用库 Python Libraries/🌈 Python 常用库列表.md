+ **链接** -  [PyPi](https://pypi.org/)、[Anaconda](https://anaconda.org/anaconda/repo)、[Conda-Forge](https://anaconda.org/conda-forge/repo)
+ **另见** - 🌈 [C++ 常用库列表](🌈%20C++%20常用库列表.md)

Python的库是提供扩展功能的一系列外部模块，分为**标准库**和**第三方库**两类，前者由Python官方维护，属于Python标准的一部分，不需要另外安装；后者由学术组织、基金会、公司维护，提供了各领域的通用框架、算法以及软件接口API，需要用`pip`或`conda`安装后方可使用

+ 🌈 **[第三方库](#第三方库%20Third%20Party%20Libraries)** - [Data](#数据分析%20Data%20Analysis) · [NN](#神经网络%20Neural%20Network) · [RL](#强化学习%20Reinforcement%20Learning) · [Robot](#机器人%20Robot) · [CV](#计算机视觉%20Computer%20Vision) · [其他](#其他)
+ 🗃 **[标准库](#标准库%20Standard%20Packages)** - 


---
## 第三方库 Third Party Libraries



### 数据分析 Data Analysis

+ 🗃 **[Numpy](https://numpy.org/doc/stable/user/index.html#user)** | `numpy` (`np`) - 更好的数组运算（[笔记](Numpy.md)）
+ 📈 **[Matplotlib](https://matplotlib.org/stable/index.html)** | `matplotlib` - 数据绘图（[笔记](📈%20Matplotlib.md)）
+ 🌊 **[Seaborn](https://seaborn.pydata.org/)** | `seaborn` - 高级数据绘图
+ 📊 **[Pandas](https://pandas.pydata.org/docs/user_guide/index.html#user-guide)** | `pandas` (`pd`) - 表格数据处理（[笔记](📊%20Pandas.md)）
+ 🎰 **[Scipy](https://docs.scipy.org/doc/scipy/reference/index.html#scipy-api)** | `scipy` - 计算优化及信号处理（）
+ 🌱 **[Scikit-learn](https://scikit-learn.org/stable/)** | `sklearn` - 传统的机器学习算法
+ 📅 **[Openpyxl](https://openpyxl.readthedocs.io/en/stable/index.html)** | `openpyxl` - Excel读写，支持编辑样式（[笔记](Openpyxl.md)）

### 神经网络 Neural Network

+ 🔦 **[PyTorch](https://pytorch.org/docs/stable/index.html)** | `torch` - 学术界常用的神经网络库（[[🔦 PyTorch 基本教程|笔记]]）
+ ♨️ **[TensorFlow](https://www.tensorflow.org/api_docs/python/tf/all_symbols)** | `tensorflow` (`tf`) - 工业界常用的神经网络库
+ 🍁 **[Keras](https://keras.io/api/)** | `keras` - 基于TensorFlow的神经网络接口
+ 💬 **[NLTK**](https://www.nltk.org/) | `nltk` - 自然语言处理库
+ 🤗 Datasets | `datasets` - 数据集处理（Hugging Face 框架）
+ 🤗 Transformer | `transformer` - NLP、模型微调（Hugging Face 框架）
+ 🤗 Evaluate | `evaluate` - 神经网络评估（Hugging Face 框架）

### 强化学习 Reinforcement Learning

+ ⛳ **[Gymnasium](https://gymnasium.farama.org/)** | `gymnasium` (`gym`) - 强化学习环境框架搭建工具
+ 🦁 **[PettingZoo](https://pettingzoo.farama.org/index.html)** | `pettingzoo` - 强化学习多智能体环境框架搭建工具
+ 🏀 **[Stable Baselines](https://stable-baselines3.readthedocs.io/en/master/)** | `stable_baselines3` - 强化学习常用算法封装

### 机器人 Robot

+ 🔫 **[PyBullet](https://pybullet.org/wordpress/index.php/forum-2/)** | `pybullet` (`p`) - 3D物理仿真器
+ 🎛 **[Control](https://python-control.readthedocs.io/en/0.10.1/#)** | `control`(`ct`) - 控制器设计、仿真、分析
+ 🚢 **[Simple PID](https://simple-pid.readthedocs.io/en/latest/user_guide.html)** | `simple_pid` - 简单PID控制器实现
+ ☄️ **[CVXPY](https://www.cvxpy.org/)** | `cvxpy`(`cp`) - 凸优化

### 计算机视觉 Computer Vision

+ 🖼 **[OpenCV](https://docs.opencv.org/4.x/d6/d00/tutorial_py_root.html)** | `cv2` - 图像处理与机器视觉（[[OpenCV Python 基本教程|笔记]]）
+ 🧊 **[Open3D](https://www.open3d.org/docs/release/)** | 
+ 📽️ **[Viser](https://viser.studio/main/)** | `viser` - 3D可视化

### 计算机网络 Computer Network

+ 📌 **[HTTPx](https://www.python-httpx.org/)** | `httpx` - HTTP客户端支持


### 其他 

+ 📝 [**PrettyTable](https://ptable.readthedocs.io/en/latest/tutorial.html)**  `prettytable` - 命令行表格
+ 🚥 **[Tqdm](https://tqdm.github.io/)** | `tqdm` - 命令行进度条
+ 🧮 **[Sympy](https://www.sympy.org/en/index.html)** | `sympy` - 数学表达式对象
+ 📦 **[Attrs](https://www.attrs.org/en/stable/)** | `attrs` - 类定义优化
+ 🎉 **[Holidays](https://github.com/vacanza/holidays)** | `holidays` - 世界各国节假日数据
+ ✒️ **[ReportLab](https://docs.reportlab.com/)** | `reportlab` - 


---
## 标准库 Standard Packages

+ **参考** - [Python标准库文档](https://docs.python.org/3/library/index.html)

+ 🖥 os | 底层文件操作
+ 💾 sys |
+ 🗂 shutil | 顶层文件操作
+ 😮 **[argparse](https://docs.python.org/3/library/argparse.html)** | 命令行参数解析（[笔记](argparse.md)）
+ 🥜 copy | 深浅拷贝控制
+ 🧩 **[typing](https://docs.python.org/3/library/typing.html)** | 类型标注
+ **[itertools](https://docs.python.org/3/library/itertools.html)** | 迭代工具
+ 🏵 re | 正则表达式
+ 🐘 abc | 抽象类支持
+ 📰 csv | CSV数据读写
+ 🎰 random | 伪随机数生成
+ 📟 math | 常用数学函数
+ ⏰ time | 时间记录与计算
+ 📆 **[datetime](https://docs.python.org/3/library/datetime.html)** | 日期支持（[笔记](datetime.md)）
+ 📅 calendar | 日历支持（）
+ 🐢 turtle | 平面轨迹绘图
+ heapq | 堆运算函数
+  | 数据容器

---
## Top Down 分类学习

+ [Python 数据分析](📊%20Python%20数据分析.md)（🗃📈🌊📊🎰🌱）
+ Python 神经网络（🔦♨🍁🤗）
+ [Python 强化学习](⛳%20Python%20Farama%20强化学习工具链.md)（⛳🦁🏀）
+ Python 机器视觉（🖼）
+ [Python 控制系统](🐍%20Python%20控制框架.md)（🎛🚢）



