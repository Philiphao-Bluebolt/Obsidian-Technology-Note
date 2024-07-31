Git是Linux之父Linus开发的开源分布式版本管理工具，可用于版本备份、分支管理、代码文本改动检测。最常见的用法是与远程代码托管平台Github联动，进行项目仓库Repository的上传备份和拉取。

Git使用Linux风格的命令行进行操作，虽然最新版本也提供了Windows CMD风格的命令行和图形化界面，但Linux风格的命令行还是更为常用。

---
## 四大区域

Git的四大区域指的是工作路径、缓存区、本地仓库、远程仓库。

1. 工作路径（Working Directory）：编程时直接操作的项目文件夹，因此会有频繁的改动；

2. 缓存区（Staging/Index Area）：文件夹.git中的一份列表，追踪工作路径中的文件改动；

3. 本地仓库（Local Repository）：位于文件夹.git中，储存所有提交的项目分支版本；

4. 远程仓库（Remote Repository）：这是Github、Gitee等代码托管平台上由你自己创建的一个文件夹，用于储存本地仓库中；

![[Pasted image 20240413152101.png]]
