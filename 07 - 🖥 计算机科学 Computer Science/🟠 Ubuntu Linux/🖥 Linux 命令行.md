+ **参考**：[官方教程](https://ubuntu.com/tutorials/command-line-for-beginners#1-overview)、[60个常用命令](https://www.youtube.com/watch?v=gd7BXuUQ91w&ab_channel=NetworkChuck)
+ 文档：📜 [Bash](https://www.gnu.org/savannah-checkouts/gnu/bash/manual/bash.html)

Ubuntu大部分操作使用命令行控制，包括文件管理、软件下载、程序执行、系统设置等，此惯例源于没有图形化界面的早期Unix系统。命令行使用的语法基于Bash或Shell脚本语言

+ 🧩 **命令行基础**

+ 📜 **脚本语言 - Bash**：总览
	+ **基本**：变量 | 函数 | 条件
	+ ****：

+ 

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

+ [[#基本命令 Basic Commands]]
	+ [[#clear - 清屏]]
	+ [[#exit - 退出命令行]]
	+ [[#man - 调出指令用户手册]]
	+ [[#whoami - 查看当前用户名]]
	+ [[#su- 切换用户]]
	+ [[#echo - 输出文本]]
+ [[#文件管理命令 File Management Commands]]
	+ [[#pwd - 列出当前工作路径（"Print Working Directory"）]]
	+ [[#cd - 改变当前工作路径（"Change Directory"）]]
	+ [[#ls - 列出目标路径的所有内容（"List Contents"）]]
	+ [[#du - 查看目录空间大小]]
	+ [[#find - 搜索文件]]
	+ [[#tree - 目录结构可视化]]
	+ [[#cp - 复制文件（"Copy"）]]
	+ [[#mv - 移动文件（”Move”）]]
	+ [[#mkdir - 创建新文件夹（"Make Directory"）]]
	+ [[#cat：查看、合并文本文件（"Concatenate"）]]
	+ [[#chmod - 文件权限设置（"Change Mode"）]]
	+ [[#ln - 创建目录符号链接]]
+ [[#网络配置命令 Network Configuration Commands]]
	+ [[#ifconfig - 查看IP地址]]
	+ [[#ping - 检查IP端口连接状态]]
	+ [[#nmcli - 网络管理器]]
+ [[#进程管理命令 Process Management Commands]]
	+ [[#top - 进程监测器]]

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




---
## 常用命令 Common Commands

这里列出Ubuntu Linux系统命令行的常用命令

### 基本命令 Basic Commands

与用户权限与命令行程序自身相关的命令

#### clear - 清屏

```bash
clear
```

#### exit - 退出命令行

```
exit
```

#### man - 调出指令用户手册

```bash
man cd
```

#### whoami - 查看当前用户名

```bash
whoami
```

#### su- 切换用户（"Switch User"）

用于切换用户，不加参数时默认切换到Superuser，直接使用`su`指令是不被允许的，可以使用`sudo su`跳过限制。

```bash
# 切换到Superuser，一般禁用
su 

# 切换到Superuser
sudo su

# 切换到<username>所指用户
su username
```

#### echo - 输出文本




### 文件管理命令 File Management Commands

文件管理命令用于文件的查找、创建、编辑、复制、删除等基本操作

#### pwd - 列出当前工作路径（"Print Working Directory"）

```bash
pwd
```

#### cd - 改变当前工作路径（"Change Directory"）

用于改变当前的工作路径

```bash
# 当前工作路径改为Home文件夹
cd /home/username
```

#### ls - 列出目标路径的所有内容（"List Contents"）

```bash
# 列出当前路径的所有非隐藏对象
ls

# 列出当前路径的所有对象（包含隐藏文件）
ls -a

# 列出Home文件夹所有对象
ls /home/username
```

#### du - 查看目录空间大小

用于查看指定目录内容占用磁盘空间的大小，默认以KB为单位，常用选项包括

+ `-h` - 以易读的单位输出
+ `-d` - 指定搜索层数（默认列出所有下级子目录）
+ `-a` - 同时列出文件及文件夹

```bash
# 以KB为单位列出当前目录下所有子目录占用磁盘大小
du 

# 以易读的单位输出当前目录下所有文件夹及文件的大小
du -h -a -d 1
```

#### find - 搜索文件

在指定目录及下级查找指定类型、名称的文件，还可指定文件大小等更复杂的搜索过滤器，常结合通配符使用。

```bash
# 在当前路径下查找所有.txt文件
find -type f -name "*.txt"

# 在路径/path/to/search下查找名为docs的文件夹
find /path/to/search -type d -name "docs"

```

### tree - 目录结构可视化

+ 安装：`sudo apt install tree`

这个命令由软件包`tree`提供，可在命令行绘出目标路径的下级文件、文件夹分支结构

```bash
tree
```

![[Pasted image 20250116150606.png]]

#### cp - 复制文件（"Copy"）

新文件可重命名，用于复制文件夹要注明`-r`

```bash
# 文件夹t1中的test.txt文件复制到文件夹t2
cp /tmp/t1/test.txt /tmp/t2

# 文件夹t1中的test.txt文件复制到文件夹t2，新文件命名为test_b.txt
cp /tmp/t1/test.txt /tmp/t2/test_b.txt

# 文件夹t1复制到t2中
cp -r /tmp/t1 /tmp/t2
```

#### mv - 移动文件（”Move”）

移动后可重命名

```bash
# 当前路径test.txt文件移动到t2文件夹
mv test.txt t2

# 当前路径test.txt文件移动到t2文件夹，并改名为test_new.txt
mv test.txt t2/test_new.txt

# 当前路径test.txt文件改名为test_rename.txt
mv test.txt test_rename.txt
```

#### mkdir - 创建新文件夹（"Make Directory"）

```bash
# 当前路径创建test_ws文件夹
mkdir test_ws

# 当前路径同时创建test_ws和src文件夹
mkdir test_ws src

# 当前路径创建test_ws，并在test_ws中创建src文件夹
mkdir -p test_ws/src
```

### touch - 创建新文件或修改文件时间戳

用于修改文件的改动和访问时间，当指定的文件不存在时会创建新文件，因此也该命令也广泛用于创建新文件，常用选项如下

+ `-c` - 不创建新文件
+ `-t` - 指定修改的时间

```bash
# 当前路径创建test.txt文件（若test.txt原本不存在）
touch test.txt

# 更新test.txt文件的访问和修改时间（test.txt已存在）
touch test.txt
```

#### rm - 永久删除文件（"Remove"）

注意，该命令执行的删除操作不可复原！常用选项如下

+ `-f` - 
+ `-r` - 删除文件夹及其内部所有下级内容
+ `-d` - 删除空文件夹（与`rmdir`相同）

```bash
# 当前路径移除test.txt文件
rm test.txt

# 当前路径同时移除test1.txt、test2.txt文件
rm test1.txt test2.txt

# 完全移除t1文件夹及内部所有下级文件、文件夹（谨慎使用！）
rm -r t1

# 强制删除根目录下所有内容（赛博自杀） 
rm -rf /*
```

#### rmdir - 删除空文件夹（"Remove Directory"）

相当于`rm -d`

```bash
# 当前路径移除test文件夹，若test非空，则执行失败
rmdir test
```

#### cat：查看、合并文本文件（"Concatenate"）

这是一个多功能的命令，其本意是“连接”

```bash
# 在当前路径创建test.py文件，执行成功后可以在命令行对文件进行逐行写入，按CTRL+C结束写入；注意，若test.py已存在则会被覆盖！
cat > test.py

# 以文本形式输出当前路径已存在的test.py文件内容；若文件不存在则报错，若文件非文本文件则可能输出乱码
cat test.py

# 将test1.py、test2.py按行首尾相接，创建main.py文件将上述相接后的文本写入其中
cat test1.py test2.py > main.py
```

#### chmod - 文件权限设置（"Change Mode"）


#### ln - 创建目录符号链接



### 网络配置命令 Network Configuration Commands



#### ping - 检查IP端口连接状态

支持IP地址和网址输入

```
ping 192.168.0.1
ping www.baidu.com
ping www.google.com
```


#### ifconfig - 查看IP地址

+ 安装：`sudo apt install net-tools`

网络端口及IP地址查看

```bash
ifconfig
```


#### nmcli - 网络管理器

Linux网络管理器命令行接口（Network Manager Command-Line Interface）

打开并刷新所有网络服务，关闭是`off`：

```bash
nmcli n on
```


#### dhclient：


#### wget：


#### curl：


### 进程管理命令 Process Management Commands

#### top - 进程监测器