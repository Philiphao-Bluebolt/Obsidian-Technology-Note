+ **参考**：[官方教程](https://ubuntu.com/tutorials/command-line-for-beginners#1-overview)、


Ubuntu大部分操作使用命令行控制，包括文件管理、软件下载、程序执行、系统设置等，此惯例源于没有图形化界面的早期Unix系统。命令行使用的语法基于Bash或Shell脚本语言

+ [[#命令行基础 Command Line Basics]]
	+ [[#命令行格式及操作 Format & Operation]]
	+ [[#快捷键 Hotkeys]]
	+ [[#路径 Directory]]
	+ [[#用户及权限 User Permission]]
	+ [[#通配符 Wildcards]]
	+ [[#管线命令及结果储存 Piping and Output Storage]]
	+ [[#控制运算符 Control Operator]]
+ [[#脚本编写 Bash Script]]
	+ [[#相关系统文件]]
	+ [[#基本语法]]
	+ [[#Shell函数 - 自定义命令]]

+ [[#常用命令 Common Commands]]



---
## 命令行基础 Command Line Basics

Unix命令的基本格式

### 命令行格式及操作 Format & Operation

Linux命令的格式是：

```
command  option  parameter1  parameter2
```

下面是一些命令行管理常用的指令：

1. `clear`：清屏
2. `exit`：退出命令行
3. `man`：调出一个指令的用户手册

### 快捷键 Hotkeys

熟练使用快捷键可以极大地提升输入效率，注意Linux命令行的快捷键与Windows系统的常用快捷键不同。

特别的，TAB键可以对指令进行自动补全。若已输入的参数有多种补全的可能性，命令行会输出一张包含所有可能选项的表格；若已输入的参数匹配不到任何选项，则自动补全无反应。

| **操作**           | **快捷键**            |
| ---------------- | ------------------ |
| 自动补全 或 列出选项      | TAB                |
| 打开新的命令行窗口        | CTRL + ALT + T     |
| 在已有的命令行窗口打开新的子窗口 | CTRL + SHIFT + T   |
| 复制/粘贴            | CTRL + SHIFT + C/V |
| 删除光标前的内容         | CTRL + U           |
| 删除光标前一个单词        | CTRL + W           |
| 终止进程             | CTRL + C/Z         |
| 滚动查看历史输入命令       | 上下键                |
| 关闭命令行            | CTRL + D           |

### 路径 Directory

类Unix系统中的路径与Windows并不相同，Windows系统以硬盘盘符`C:`、`D:`为起始根目录，而Linux中仅有一个根目录“/”，另外，Linux以“/”作为路径分隔符。

在文件夹中右键打开终端时，默认起始工作路径为当前文件夹路径。

Linux同时支持绝对和相对路径。

+ 绝对地址：以斜杠`/`开头，表示根目录；注意访问`home`文件夹的目录还要在后面加上一层用户名。

+ 相对路径：以当前工作路径为参照；两点`..`表示上一级目录，一点`.`表示本级目录

常用的路径符：

| **目录表示** | **符号**                      |
| -------- | --------------------------- |
| 根目录      | `/ `（斜杠）                    |
| Home目录   | `~` （波浪线）或 `/home/username` |
| 上一级目录    | `..` （两点）                   |
| 当前目录     | `. `（一点）                    |

### 用户及权限 User Permission

用户权限相关的命令有`whoami`、`su`、`sudo`、`chmod`等。

Linux系统中默认有名为`root`的超级用户（Superuser），这个用户拥有执行一切命令、修改一切文件的最高权限，可能会对系统造成无意的破坏，因此以`root`的身份执行命令有一定的风险，正常使用时以普通用户身份运行即可。

Linux下需要`root`权限的常见操作：安装/删除程序、更改磁盘容量、修改系统文件

![[Pasted image 20240420112833.png]]

### 通配符 Wildcards

通配符（Wildcards）常见于文件的批量操作，可用于模糊选定位于同一目录中一系列名称相似的文件及文件夹。

1. `*`（星号）：表示该位置及之后的字符任意

移除当前目录所有以te开头的文件（te开头的文件夹也会被选中，只是rm不支持删除文件夹）

```bash
rm  te*
```

连接并输出所有test开头的文件

```bash
cat  test*
```

2. `?`（问号）：表示当前位置可为任意字符

移除当前目录所有名称符合该结构的文件

```bash
rm  tmp?.txt
```


### 管线命令及结果储存 Piping and Output Storage

+ 管线命令（Command Piping）：一种多命令数据传送格式，在同一行中用`|`隔开多个不同的指令，前一个指令的输出结果将作为后一个指令的输入参数。

+ 结果储存：利用`>`（大于号），可以将文本输出结果写入到指定的文件中；若文件不存在则会创建新文件，若文件已存在则会被覆盖。这种写法运行时，输出结果**不会**打印到命令行中。

```bash
cat  test.txt  |  sort  |  uniq  >  processed_data.txt
```

在上面的命令中，`cat`输出`test.txt`文件的文本内容，`sort`接受`cat`的运行结果作为输入并输出排序后的文本内容，`uniq`则输出删去相邻重复行的文本内容，文本内容最后写入文件`processed_data.txt`中。在完整的运行过程中，`test.txt`中的文本逐级传输，经过了两次处理。


### 控制运算符 Control Operator

在Linux命令行中，控制运算符（Control Operator）可用于改变指令的行为，并建立多条命令、命令与文件之间的互动关系。

| 运算符  | 使用格式                       | 解释                                      |
| ---- | -------------------------- | --------------------------------------- |
| &&   | `command1 && command2`     | 多条指令连续执行，`command1`执行成功才执行`command2`    |
| \|\| | `command1 `\|\|` command2` | 与&&类似，但是在`command1`执行失败时才继续执行`command2` |
| ;    | `command1 ; command2`      | 无条件多指令连续执行                              |
| \|   | `command1 `\|` command2`   | 管线命令，`command1`输出作为`command2`的输入参数      |
| >    | `command > file`           | command的输出写入`file`中，且会覆盖掉同名文件           |
| >>   | `command >> file`          | 与>类似，但是若`file`已存在，则在已有文本后面写入而非直接覆盖      |
| <    | `command < file`           | 将`file`的内容作为`command`的输入参数              |

---
## 脚本编写 Bash Script

在Linux系统下的bash是一种Shell脚本语言，即命令解释性脚本语言，可以把它简单理解成一个指令的清单，命令行执行.bash脚本文件时，会按顺序一行行地执行文件中编写的命令。

Ubuntu常见的Shell脚本语言有bash和sh，以bash为默认解释器。由于bash指令是sh的超集，bash解释器可以同时运行.bash和.sh文件，sh解释器则不一定能很好地执行.bash文件。

编写bash脚本文件的时候，开头要有一行“#!/bin/bash”，表示该文件应由bash解释器运行。在某些应用场景下（.server文件指向的脚本），若缺少这行代码会导致报错。

### 相关系统文件

+ `/home/<username>/.bashrc` - 里面的命令在打开命令行时自动执行；
+ `/home/<username>/.bash_history` 命令历史记录

### 基本语法

+ `# text` - 注释


### Shell函数 - 自定义命令

Shell函数可以用来定义全新的命令（下面的例子中是`my_cmd`），一般在`.bashrc`中使用，`$1, $2, $3 ... $n`表示运行指令时第n个输入参数的引用

```bash
my_cmd(){
	echo "Hello $1! $2! $3!"
}
```

调用时用空格区分参数

```bash
my_cmd "World" "Ubuntu" "Linux"
```

输出文本如下

```bash
Hello World! Ubuntu! Linux!
```


### 

export 变量

alias 命令简写

~/.bash_aliases 



