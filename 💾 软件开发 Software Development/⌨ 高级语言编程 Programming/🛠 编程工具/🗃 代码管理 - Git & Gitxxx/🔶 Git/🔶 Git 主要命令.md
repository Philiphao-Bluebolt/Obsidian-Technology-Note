
![[Pasted image 20240805222342.png]]

+ 配置及提示
	+ [[#help]] - 命令格式及选项帮助
	+ [[#config]] - Git配置
	+ [[#init]] - 初始化文件夹
+ 版本管理
	+ [[#status]] - 缓存区文件追踪状态
	+ [[#add]] - 提交记录到缓存区
	+ [[#reflog]] - 本地仓库操作历史
	+ [[#commit]] - 提交到本地仓库
	+ [[#reset]] - 本地仓库版本历史回退（岁月史书）
	+ [[#restore]] - 工作区回退到指定仓库版本（不改变仓库记录）
+ 分支管理
	+ [[#branch]] - 分支显示、创建、移除
	+ [[#switch]] - 命令行切换当前分支
	+ [[#merge]] - 分支合并（到当前分支）
	+ [[#rebase]] - 分支基前移
+ 远程同步
	+ [[#remote]] - 远程连接源显示、创建、移除
	+ [[#push]] - 本地仓库 --> 远程仓库
	+ [[#pull]] - 远程仓库 --> 本地仓库 & 工作区
	+ [[#fetch]] - 远程仓库 --> 本地仓库
	+ [[#clone]] - 拉取远程仓库拷贝

使用频率较低或过时的命令，如`rm`、`clean`、`checkout`等不列出

---
## help

命令`git help`用于打印命令格式和选项列表

```bash
git  help
```

![[Pasted image 20240803223124.png]]

---
## config

命令`git config`用于Git的全局（Global）或此仓库（Local）底层配置修改，比如提交使用的用户名、邮箱设置

+ `--local` 表示此仓库配置，覆盖全局设置
+ `--global`表示全局设置，适用于本机所有Git仓库

配置用户名、邮箱，详见[[配置 - 名称和邮箱]]

```bash
# 修改此仓库提交使用的用户名、邮箱
git  config  --local  user.name  my_name
git  config  --local  user.email  my_email@xxx.com
```

配置代理服务器

```bash
git  config  --global  http.proxy  
```

---
## init

命令`git init`用于在当前文件夹中创建Git本地仓库

```bash
# 将当前文件夹初始化为Git文件夹
git  init
```

---
## status

命令`git status`用于检查缓存区提交状态

```bash
git  status
```

未提交的编辑（M）、删除（-）和未追踪的新文件（+）显示红色，已提交的则显示绿色

![[Pasted image 20240804094444.png]]

![[Pasted image 20240804094458.png]]

---
## add

命令`git add`用于提交工作区的改动到缓存区

```bash
# 所有工作区改动提交到缓存区
git  add  .

# 文件file1.txt的改动提交到缓存区
git  add  file1.txt
```

要移除缓存区的记录，使用`git  restore  --staged  .`

---
## reflog

命令`git reflog`用于输出本地仓库所有修改历史（包含所有分支），以及操作涉及的版本号，不包含缓存区的改动，按Q退出

```bash
git  reflog
```

![[Pasted image 20240803222859.png]]

---
## commit

命令`git commit`用于将缓存区的修改提交到本地仓库，创建一个新版本

```bash
# 需要附上提交备注
git  commit  -m  "Create a file xxx.txt"
```

---
## reset

命令`git reset`用于回退本地仓库的版本提交历史，同时将工作区和缓存区的状态恢复到回退版本，具体回退方式取决于参数：

+ `--soft` - 不改变工作区和缓存区
+ `--mixed` - 清空缓存区，保留工作区修改
+ `--hard` - 清空工作区和缓存区所有新的修改，**不会移除工作区内未提交到缓存区的新增文件**

可以用`HEAD`指代版本：

+ `HEAD` - 最新的提交版本（上一次提交）
+ `HEAD~` - 倒数第二次提交版本
+ `HEAD~<4>` - 倒数第四次提交版本

```bash
# 回退工作区和缓存区所有新的修改到上一次提交版本，实际上没有改变本地仓库的版本提交历史
git  reset  --hard  HEAD

# 回退本地仓库的版本到前一次提交版本（即移除上一次提交），清空缓存区，保留工作区修改
git  reset  --mixed  HEAD~
```

---
## restore

命令`git restore`用于将工作区内**未提交到缓存区的修改**回退到特定提交版本，对已提交到缓存区的修改无效，且不会移除新增（+）的文件

要移除新增（+）文件只能手动操作或使用`git clean`（移除新增的未缓存文件）

```bash
# 回退工作区未缓存的删除（-）、编辑（M）操作到上一次提交版本，不影响新增文件（+）
git  restore  .

# 回退到仓库提交版本930a54
git  restore  .  --source  930a54
```

该命令也用于移除缓存区的提交

```bash
# 将file1.txt移出缓存区
git  restore  --staged  file1.txt

# 清除所有缓存区的提交
git  restore  --staged  .
```

与`git reset`不同，该命令不会影响本地仓库的版本历史，相当于一个安全版的`git reset`

---
## branch

命令`git branch`用于本地仓库分支的操作

```bash
# 创建新分支new_branch（不会切换）
git  branch  new_branch  

# 列出本地仓库中所有分支
git  branch  -l  

# 删除分支new_branch
git  branch  -d  new_branch  
```

---
## switch

命令`git switch`用于在命令行中切换当前操作的活跃分支

```bash
# 切换到分支new_branch
git  switch  new_branch
```

---
## merge

命令`git merge`用于将其他分支合并到当前分支，同时创建一次新的提交

```bash
# 将分支dev合并到当前分支
git  merge  dev
```


---
## rebase

命令`git rebase`用于将一个分支的分叉点后移，从而同步主分支的最新提交

```bash
# 将dev分支在master主分支的分叉基版本前移到master的最新提交版本
git  rebase  master  dev
```


---
## remote

命令`git remote`用于远程仓库源URL的配置和修改

```bash
# 添加源，命名为origin
git  remote  add  origin  https://github.com/my_username/my_repo.git

# 删除源
git  remote  remove  origin
```

---
## push

命令`git push`用于将本地仓库上传到远程仓库，需要指定分支

```bash 
# 本地仓库的master分支上传到origin源指向的远程仓库
git  push  -u  origin  master
```

---
## pull


---
## fetch



---
## clone

命令`git clone`用于将远程仓库整体拷贝到本地

```bash
# 将Github上的my_repo仓库整体拷贝到当前文件夹
git  clone  https://github.com/my_username/my_repo.git
```