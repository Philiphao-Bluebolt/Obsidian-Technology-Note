

---
## 快捷键

| 快捷键                | 功能  |
| ------------------ | --- |
| CTRL + ENTER       | 换页符 |
| ALT + “+“          | 公式  |
| CTRL + SHIFT + “+“ | 上标  |


---
## 同一行字符部分右对齐

+ **参考**：[Zhihu](https://www.zhihu.com/question/35545691)

在一行的最右侧双击鼠标，光标会自动右对齐，新输入的字符全部右对齐，不会影响到同一行里之前输入的左对齐的字符。

---
## 公式居中编号右对齐

+ **参考**：[公式居中、编号右对齐、自动编号、交叉引用](https://blog.csdn.net/qq_38246166/article/details/135580981?ops_request_misc=&request_id=&biz_id=102&utm_term=word%E5%85%AC%E5%BC%8F%E5%B1%85%E4%B8%AD%E5%8F%B3%E5%AF%B9%E9%BD%90&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-135580981.nonecase&spm=1018.2226.3001.4187)

常见的论文格式要求数学公式居中，公式的编号右对齐；难点在于Word默认的格式规定数学公式同一行有非公式内容时，公式会左对齐，这一段就是要解决这个问题。

![[Pasted image 20240513154448.png]]

1. 查看纸张宽度：“布局-纸张大小”，记下纸张宽度$w=21cm$
2. 查看左右的页边距：“布局-页边距”，记下$l_{left}=3cm,l_{right}=3cm$
3. 创建并修改新样式：“开始-样式-创建样式”
4. 设置制表位：“修改样式-格式-制表位”，创建两个制表位
$$居中对齐=\frac{w-l_{left}-l_{right}}{2}$$
$$右对齐=w-l_{left}-l_{right}$$
输入公式，在公式的左右分别打一个制表符（TAB），就可以看到公式右侧的内容自动右对齐了

