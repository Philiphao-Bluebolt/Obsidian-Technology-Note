Git在本地默认只使用一个账号，实际开发时常使用多个Github账号，将工作和私人的代码分开储存，因此需要设置Git在上传不同仓库时使用不同账号

Github通过SSH密钥对的公钥（而不是账户名或邮箱）判断Git正在使用的账号，配置SSH在连接不同的Host时使用**不同的密钥**，即可实现Git一机多号

假设需要设置的两个Github账号分别为“Bluebolt”和“Beam”，原理图如下：

![[Pasted image 20240728172233.png]]

同一设备登录多个Github账号可以在网页右上角快速切换

![[Pasted image 20240728173122.png]]

+ 步骤
	+ [[#生成密钥对]]
	+ [[#添加公钥到Github账户]]
	+ [[#配置config文件]]
	+ [[#测试连接]]
		+ [[#问题 - Git Bash连接失败]]

---
## 生成密钥对

`.ssh`文件夹路径：

+ Windows - `C:/Users/${User}$/.ssh`
+ Linux - `~/.ssh`

在`.ssh`文件夹中以管理员身份运行git bash，为两个账号分别生成一组密钥，备注注明邮箱

```bash
ssh-keygen -t rsa -f C:/Users/${User}$/.ssh/Bluebolt-rsa -C "email_1"
ssh-keygen -t rsa -f C:/Users/${User}$/.ssh/Beam-rsa -C "email_2"
```

其中生成的`.pub`文件是密钥对的公钥，没有后缀的文件是私钥

---
## 添加公钥到Github账户

+ Github账号设置：Setting >> Access - SSH and GPG keys >> New SSH Key

把公钥文件的内容复制到Key一栏中，Key Type选择Authentication Key，Title任取

![[Pasted image 20240801170744.png]]

---
## 配置config文件

在`.ssh`路径创建config文件，不同的Host使用不同的密钥，对应不同的账户，但是映射到相同的域名`github.com`

+ `Host` - 使用的别名
	+ `HostName` - 实际映射域名
	+ `User` - 登陆用户名（全部默认为`git`）
	+ `IdentityFile` - 相应密钥私钥文件

```config
Host bluebolt.github.com
	HostName github.com
	User Bluebolt
	PreferredAuthentications publickey
	IdentityFile C:\Users\${User}$\.ssh\Bluebolt-rsa

Host beam.github.com
	HostName github.com
	User Beam
	PreferredAuthentications publickey
	IdentityFile C:\Users\${User}$\.ssh\Beam-rsa
```

---
## 测试连接

在Git Bash中用以下命令测试能否连接到指定账户

```bash
ssh -T git@beam.github.com
```

### 问题 - Git Bash连接失败

如果在Windows 命令行中连接成功，而在Git Bash中连接失败，则Git可能没有使用Windows系统中的OpenSSH配置

+ 解决方案：将上述对config文件的修改改为在`Git/etc/ssh/ssh_config`配置文件中进行

![[Pasted image 20240730150800.png]]

---
## 设置仓库的用户名和邮箱

使用两个账户时，每个仓库都要设置自己的用户名和邮箱，详见：[[配置 - 名称和邮箱]]