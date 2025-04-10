+ **需求**：整个仓库所有文件的 Wikilink 转换为 MDlink
+ **工具**：Python

Obsidian默认的页面链接使用Wikilink格式而非Markdown普遍通用的MDLink格式，需要实现这两者的互换。

MDLink的页面名称必须使用纯URL格式，意味着

Wikilink - `[[页面名称#标题|显示文本]]` 
MDLink - `[](页面名称.md#标题)`

+ **难点**
	+ 找出链接：找出页面中所有Wikilink链接，可使用正则表达式（这是什么？）
		+ 页面链接：`[[]]`
		+ 多媒体链接：`![[]]`
		+ 例外：代码块和数学公式内出现的双中括号不能被识别为链接
	+ URL格式转换：页面名称和标题名称必须转换为URL格式，可使用`urllib.parse.quote()`
	+ 页面路径：Wikilink允许仓库内不重名页面省略路径，转换为MDLink时必须标上路径
		+ 路径搜寻：需要搜索引用页面的相对位置
		+ 直接转换：如果已经是路径（包含`/`）或者引用页面就在同一路径，直接转成URL即可

+ **特殊处理**
	+ 不转换文本块引用：Wikilink支持使用`^`引用文本块，MDLink无此功能，因此不予转换


