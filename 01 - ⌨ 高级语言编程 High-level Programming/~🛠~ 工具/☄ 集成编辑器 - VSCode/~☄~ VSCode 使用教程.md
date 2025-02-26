+ 官网：[Visual Studio Code](https://code.visualstudio.com/)（需要科学上网）
+ 文档：[Documentation](https://code.visualstudio.com/docs#vscode)

VSCode是微软开发的开源代码编辑器，由于其开源的特性，用户可以安装插件、配置环境将它打造成一个轻量好用的**跨语言智能集成开发平台**（IDE）

+ **编译配置**
	+ [[#Python]]
	+ [[#C++]]
	+ [[#Java]]
+ **常用功能**
	+ [[#Copilot 辅助编程]]
	+ [[#Git 版本管理]]
	+ [[#SSH 远程开发]]
+ **其他**
	+ [[#快捷键]]

---
## Python



---
## C++



---
## Java


---
## Copilot 辅助编程



---
## Git 版本管理

基于Git的版本管理是VS Code默认提供的功能，用户可以通过图形化界面追踪工作空间内每一个文件的Git同步状态，支持文本文件的改动比较以及一键回滚

![[Pasted image 20250219103647.png]]

---
## SSH 远程开发

+ **所需扩展**：Remote - SSH

SSH扩展让用户可以指定IP地址远程登陆计算机，访问其命令行和文件管理系统，并在VScode中编辑存放在远端计算机的源代码

启动SSH扩展的按钮在界面的左下角：

![[Pasted image 20250219102329.png]]

1. **打开配置文件**：“打开远程窗口” --> ”连接到主机“ --> “配置SSH文件”
	+ Windows - `C:/Users/xxx/.ssh`
	+ Ubuntu - `~/.ssh`

2. **新建远程主机**：按一下格式填写目标地址`HostName`及用户名`User`

```config
Host Ubuntu
  HostName 192.168.189.128
  User beam
```

3. **连接**：输入操作系统类型（首次登录）、用户登录密码

---
## 快捷键

|     |     |
| --- | --- |
|     |     |
