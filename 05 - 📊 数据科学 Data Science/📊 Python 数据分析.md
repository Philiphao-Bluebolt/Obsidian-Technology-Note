
Python是数据科学领域最常用的语言之一，大量的第三方库提供了数据导入导出、可视化、清洗、模型训练等功能。


+ 🗂 **常用库**
	+ 处理：🗃 [Numpy](https://numpy.org/doc/stable/user/index.html#user) | 📊 [Pandas](https://pandas.pydata.org/docs/user_guide/index.html#user-guide) | 🎰 [Scipy](https://docs.scipy.org/doc/scipy/reference/index.html#scipy-api)
	+ 绘图：📈 [Matplotlib](https://matplotlib.org/stable/index.html) | 🌊 [Seaborn](https://seaborn.pydata.org/)
	+ 训练：🌱 [Scikit-learn](https://scikit-learn.org/stable/) | 🍁 [Keras](https://keras.io/api/) | ♨ [TensorFlow](https://www.tensorflow.org/api_docs/python/tf/all_symbols) | 🔦 [PyTorch](https://pytorch.org/docs/stable/index.html)
+ 📝 **数据结构**
	+ 数组：[NDArray](#Numpy%20NDArray) | [DataFrame](#Pandas%20DataFrame) | [Torch Tensor](#Torch%20Tensor) | [TF Tensor](#TF%20Tensor)
	+ 树图：
+ 💾 **数据读写**：
	+ 导入：
	+ 导出：

+ ****

+ 

+ 🎨 **绘图展示**：








---
## 数据结构

数据分析领域最常见的数据结构是数组，包括一维的向量，二维的表格、矩阵，以及包含更复杂信息的高维数组。与数学中的张量相似，每个数据集中包含的数值在数组之中以**网格**状排列成**超立方体**形状。

在某些场景中，也会使用树和图作为储存数据的容器。

### Numpy NDArray

+ **文档**：[np.ndarray](https://numpy.org/doc/stable/reference/arrays.ndarray.html#)

Numpy的多维数组类型提供了多样的数据操作函数和方法，运算速度亦比原版列表更快，因此是Python数据处理最常用的数组类型

使用`shape`属性可以检查数组各维度下的长度

> [!hint] Numpy 数组创建
> + 全零：`np.zero((m, n, k))`（形状为`m*n*k`的三维全零数组）
> + 全一：
> + 周期重复：`np.tile(arr, (m, n))`（原有数组`arr`以`m`行`n`列形式重复）
> + 

> [!hint] Numpy 数组常用操作（示例数组为`arr`）
> + **变形**：
> 	+ 扁平化：`np.ravel(arr)`（压扁成一维数组）
> + **截取**：
> 	+ 
> + **合并**：
> 	+ 列合并：`np.column_stack`
> + **算数**：
> 	+ 转置：`np.linalg.inv(arr)`
> 	+ ：
>   















### Pandas DataFrame

+ **文档**：[pandas.DataFrame](https://pandas.pydata.org/docs/reference/frame.html#)

`DataFrame`是Pandas使用的表格数据格式


如何选择特定行与列

iloc
loc
to_numpy
plot

drop 


quantile


### Torch Tensor

+ **文档**：
+ **参见**：[🔦 PyTorch 教程](🔦%20PyTorch%20基本教程.md)


### TF Tensor


---
##
### 表格

+ 相关函数：[Pandas IO](https://pandas.pydata.org/docs/user_guide/io.html)

表格是数据最常见的储存结构，常见的文件类型包括`.xlsx`、`.csv`等，可以使用 📊`Pandas` 库实现表格数据的导入及导出




### 



