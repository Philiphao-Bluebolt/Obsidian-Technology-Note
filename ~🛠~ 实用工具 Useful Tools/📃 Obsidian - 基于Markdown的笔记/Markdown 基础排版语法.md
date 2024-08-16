Obsidian的笔记是以Markdown格式标记语言为基础的。与Word等富文本编辑器不同，用Markdown语言记录的文本文件可以在任何文本编辑器中打开，且只要装有Markdown的渲染器就能正确渲染出排版效果。

标记排版语法会占用一些字符，需要使用这些字符本身的时候，就需要使用反斜杠“\”转义。

- Markdown官方格式简表：[Markdown Cheat Sheet](https://www.markdownguide.org/cheat-sheet/)
- Obsidian教程：[Basic formatting syntax](https://help.obsidian.md/Editing+and+formatting/Basic+formatting+syntax)

[[#文本块 Paragragh]]
[[#标题 Heading]]
[[#斜体、粗体、删除线 Italic & Bold & Strikethrough]]
[[#无序列表、有序列表 Unordered & Ordered List]]
[[#水平分隔线 Horizontal Rule]]
[[#代码块 Code Block]]
[[#引用块 Blockquotes]]
[[#超链接 Hyperlink]]
[[#表情 Emoji]]

---
## 文本块 Paragragh

一段文字被视为独立文本块的前提是，它的前后至少都要有一行空行，因此任何的排版结构前后都必须至少有一行空行，否则在阅读模式下可能会出现渲染错误。

---

这是一个文本块/段落。

这是另一个文本块/段落。

---

在社区中，文本块也经常被称为“段落”。

## 标题 Heading

行首一个或多个井号`#`加空格代表这一行是标题，一个井号代表一级标题，三个井号代表三级标题，最多支持六级标题。

---
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题
---
## 斜体、粗体、删除线 Italic & Bold & Strikethrough

星号`*`括住的内容表示斜体，双星号`**`括住的内容表示粗体，双波浪线`~~`括住的内容上会有删除线。

---

*斜体*
**粗体**
~~删除线~~

---
## 无序列表、有序列表 Unordered & Ordered List

行首的星号`*`或加号`+`或减号`-`加空格代表这一行是一个无序列表，在Obsidian中渲染成一个小圆点加缩进。使用时不要混用三个符号，要是用加号，同一个列表就全部用加号不要混用减号或者星号，否则会出现排版问题。

---

* 星号标注
+ 加号标注
- 减号标注

---

行首的数字、英文句号`.`或后半括号`)`加空格代表这一行是一个有序列表

---

1. 格式一
2. 格式一
1) 格式二
2) 格式二

---
在Obsidian中，列表的下面新开一行也默认是无序列表。

## 水平分隔线 Horizontal Rule

空行里三个以上的减号`-`就形成一条水平分隔线，如下所示：

---
## 代码块 Code Block

反单引号“\`”括起来的内容自动识别为代码

---

C++可以用`std::cout << a << std::endl` 在命令行打印一个变量值

---

多行的代码块用三重反单引号括起来表示，在起始的三重反单引号后面注上使用的语言（如cpp、python、bash），可以实现代码渲染

```cpp
include <iostream>
using namespace std;

int main()
{
	double a = 0.8;
	cout << "a = " << a << endl;
	return 0;
}
```

## 引用块 Blockquotes

行首的部分用大于号`>`会将这一行文字放入引用块中，引用块的内部支持嵌套的引用块，用多个大于号`>>`表示。

---
>“千里之行，始于足下”
>
>>可以像这样
>>嵌套引用
---

## 超链接 Hyperlink

创建超链接的格式是中括号名称、小括号地址：`[链接显示名称](链接地址)`。如果要创建本地文件的链接，链接地址是以本文件出发的相对路径；如果要链接到外部网站，链接地址就是网址。

---

+ 外部网站链接：[Markdown Guide](https://www.markdownguide.org/getting-started/)
+ 内部文件链接：[数学公式](LaTeX%20数学公式语法.md)
+ 本文件标题链接：[引用块 Blockquotes](## 引用块 Blockquotes)

---

Obsidian有自己的内部文件链接语法，使用双中括号`[[]]`，支持链接到仓库内文件、标题、文本块。不过，要注意这个不是Markdown的通用语法。

---

+ 链接到同一仓库中的其他文档：[[Obsidian 扩展语法]]
+ 链接到同一文档中的某个标题：[[#文本块 Paragragh]]

---
## 表情 Emoji

在Windows 10系统，可以按Win + .插入表情