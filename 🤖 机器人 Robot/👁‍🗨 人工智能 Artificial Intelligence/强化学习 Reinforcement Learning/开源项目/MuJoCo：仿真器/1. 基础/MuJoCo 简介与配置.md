MuJoCo是Roboti LLC公司开发的一款基于C++的机械仿真软件，是目前最流行的强化学习仿真软件之一。2022年被Google Deepmind收购以后，MuJoCo成为开源免费软件，但新旧版之间出现了不少兼容性问题。

![[Pasted image 20240423163706.png]]

+ Roboti LLC公司旧官网（2.0.0版本以前）：[https://www.roboti.us/index.html](https://www.roboti.us/index.html)

+ 新版本Github下载（2.0.0版本以后）：[https://github.com/google-deepmind/mujoco/releases](https://github.com/google-deepmind/mujoco/releases)
+ 新MuJoCo官网：[https://mujoco.org/](https://mujoco.org/)

原版的MuJoCo基于C++，而大多数的机器学习开发项目使用Python，因此一般在Python上编写控制代码，需要接口库作为中继才能在Python中控制MuJoCo。

最新版本的`mujoco_py`已经停止了对Windows系统的支持，因此在Windows系统上能用的`mujoco_py`对应MuJoCo版本停留在了2.1.0。

配合ROS，MuJoCo一般在Ubuntu系统使用

---
## 配置（Ubuntu 20.04）

+ 参考文章：[ubuntu20.04下安装mujoco、mujoco-py、gym](https://blog.csdn.net/qq_45480201/article/details/132585611?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522171359276616800222892903%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=171359276616800222892903&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-1-132585611-null-null.142^v100^pc_search_result_base2&utm_term=%E5%9C%A8ubuntu20.04%E4%B8%AD%E5%AE%89%E8%A3%85mujoco&spm=1018.2226.3001.4187)

安装完成后，在`~/.bashrc`文件中加入下面的函数就可以在任意位置用命令`mujoco`打开MuJoCo，后面输入文件地址还可以直接打开文件

```bash
mujoco(){
    ~/.mujoco/mujoco210/bin/simulate $1
}
```

---
## Python接口

MuJoCo的Python接口库主要有两个，`mujoco`和`mujoco_py`

+ `mujoco`：由MuJoCo官方开发维护，2022年推出
+ `mujoco_py`：由OpenAI开发维护，比较老，教程文档多，但目前似乎已经停止更新
