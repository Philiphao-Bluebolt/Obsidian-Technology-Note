+ **参考** - [Wikipedia](https://en.wikipedia.org/wiki/HTML)
+ **教程** - [W3Schools](https://www.w3schools.com/html/) | [Mozilla Doc](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements)

📑 HTML（Hypertext Markup Language，超文本标记语言） 是一种用于定义网页内容结构与布局的标记语言，以尖括号标签`<tag>`规定的元素作为基本结构描述网页的内容与布局。HTML 源码对应的文件类型为`.html`文件，浏览器和网络服务器程序可以打开`.html`文件并按照定义的格式渲染出网页内容。

🎨 [**CSS**](🎨%20CSS.md) 是 HTML 配套使用的样式定义语言，用于指定网页元素的设计风格。

+ ✨️ [**结构范例**](#✨️%20结构范例%20Structure)
+ 🧩 [**基本元素**](#🧩%20基本元素%20Common%20Element)
	+ [与 MD 对比](#与%20Markdown%20对比)


---
## ✨️ 结构范例 Structure

HTML 文件起始于一个标记语言类型声明`<!DOCTYPE html>`，其主要内容包含在三个元素中，分别是`<head> <style> <html>`。

+ `<head>` - 定义 HTML 页面的标题、缩略图、外部 CSS 文件指定的样式。
+ `<style>` - 内部定义 CSS 样式（优先级高于外部 CSS 文件）
+ `<html>` - 定义 HTML 文件的主体内容

```html
<!DOCTYPE html>
<head>
    <title>My Resume</title>
    <link rel="icon" type="image/png" size="32x32" href="images/icon.png">
    <link rel="stylesheet" href="styles/main.css">
</head>

<style>
.my_class {
	font-size: large;
    width: 600px;
    height: 100px;
    background-color: pink;
}
</style>

<html>
	<body>
		
	</body>
</html>


```

---
## 🧩 基本元素 Common Element

这里列举HTML的常用元素，元素用尖括号标签对`<element> </element>`标识，空元素（如`<br>` 、`<hr>`）则单独出现不需要加末尾括号。

### 元素清单 Element List










### HTML 与 Markdown 对比

HTML与Markdown有明显的联系，有不少

| 内容   | HTML                     | MD                  |
| ---- | ------------------------ | ------------------- |
| 分隔线  | `<hr>`                   | `---`               |
| 一级标题 | `<h1>Title</h1>`         | `# Title`           |
| 二级标题 | `<h2>Title</h2>`         | `## Title`          |
| 三级标题 | `<h3>Title</h3>`         | `### Title`         |
| 段落   | `<p>The paragraph</p>`   | 无（空白行自动分段）          |
| 换行   | `First<br>Second`        | `First\Second`      |
| 斜体   | `<i>Italics Content</i>` | `*Italics Content*` |
| 加粗   | `<b>Bold Content</b>`    | `**Bold Content**`  |
| 无序列表 | `<ul><li>Line</li></ul>` | `+ Line` 或 `- Line` |
| 有序列表 | `<ol><li>Line</li></ol>` | `1. Line`           |
| 行内代码 | `<code>print()</code>`   | \`print()\`         |
| 代码块  |                          | \`\`\`\`\`\`        |
| 超链接  | `<a> </a>`               |                     |
| 图片   |                          |                     |
|      |                          |                     |



### 保留输入格式 `<pre>`

```html
<pre> 
Rose is red
Violets are blue
</pre>
```

### 无序列表`<ul>`

```html
<ul>
	<li>Physics</li>
	<li>Chemistry</li>
	<li>Biology</li>
</ul>
```

### 有序列表`<ol>`

```html
<ol>
	<li>Physics</li>
	<li>Chemistry</li>
	<li>Biology</li>
</ol>
```

### 表格`<table>`

```html
<table>
	<tr>
		<th>Date</th>
		<th>Project</th>
		<th>State</th>
	</tr>
	<tr>
		<td>2026/01/24</td>
		<td>Website Development</td>
		<td>Working in Progress</td>
	</tr>
</table>
```


---
