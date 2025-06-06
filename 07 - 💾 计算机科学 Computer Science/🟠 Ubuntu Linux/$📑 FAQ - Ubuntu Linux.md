
+ 运行故障
	+ [[#虚拟机无法连接网络]]
	+ [[#虚拟机复制粘贴不起作用]]
	+ [[#Apt无法连接ROS源]]



---
## 虚拟机无法连接网络

+ 具体问题：右上角网络标志显示为问号

**解决方案：**

+ 重启宿主机和虚拟机（简单粗暴）
+ 关闭虚拟机VPN网络代理
+ 重启网络服务

```
nmcli n off
nmcli n on
```

+ 关闭隐私的连接性检查


---
## 虚拟机复制粘贴不起作用

+ 虚拟机 --> 主机不起作用，试试连续按两次`Ctrl` + `C` 
+ 主机 --> 虚拟机不起作用，记住不能直接复制到桌面，一定要复制到打开的文件夹窗口里



---
## Apt无法连接ROS源

+ 具体问题：`apt`无法连接ROS官网的插件仓库`package.ros.org`

```bash
Cannot initiate the connection to packages.ros.org

W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://packages.osrfoundation.org/gazebo/ubuntu-stable focal InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 67170598AF249743

```

**解决方案**

+ 更新`apt-key`的ROS源密钥
+ 开启VPN
+ 换源（据说换源也是导致密钥出问题的原因）

**最终有效的解决方案**

+ [有关ROS下相关ros包无法下载的解决方案](https://blog.csdn.net/qq_43725844/article/details/104296793?ops_request_misc=&request_id=&biz_id=102&utm_term=packages.ros.org&utm_medium=distribute.pc_search_result.none-task-blog-2~all~s)

**密钥相关配置**

+ [安装ROS，GPG错误：公匙不可用，无法验证签名解决方法](https://blog.csdn.net/m0_62838993/article/details/134803387?ops_request_misc=&request_id=&biz_id=102&utm_term=ros%20The%20following%20signatures%20c&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-134803387.142^v100^pc_search_result_base2&spm=1018.2226.3001.4187)
+ [ROS 踩坑录（一）](https://blog.csdn.net/miamo_29/article/details/96349158?ops_request_misc=&request_id=&biz_id=102&utm_term=Failed%20to%20fetch%20http://package&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-6-96349158.142^v100^pc_search_result_base2&spm=1018.2226.3001.4187)
+ [apt update fails / cannot install pkgs: key not working?](https://answers.ros.org/question/325039/apt-update-fails-cannot-install-pkgs-key-not-working/)

