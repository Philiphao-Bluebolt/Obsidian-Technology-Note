 Apt（`apt`）全称为Advanced package tool，是Debian分支Linux的命令行软件下载工具，使用时需要Superuser权限


---
## 添加下载源（）


---
## 


---
## 更新软件包（`apt update` & `apt upgrade`）

这里用到两个很相似的选项`update`和`upgrade`

更新软件包**列表**；这个命令用于从所有下载源获取最新的软件包版本列表，在下载新软件包之前也会使用这个命令以确保`apt`的软件包版本是最新的

```
sudo  apt  update
```

更新软件包；将所有软件包更新到可用的最高版本

```
sudo  apt  upgrade
```

---
## 下载软件包（`apt install`）

```
sudo  apt  install  xxx
```
