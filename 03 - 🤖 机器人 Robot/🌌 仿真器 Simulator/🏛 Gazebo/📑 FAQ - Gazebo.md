
+ **Harmonic**
	+ [[#渲染异常]]
+ **Fortress**


---
## 渲染异常

+ 版本：Harmonic、Fortress

使用`gz sim`命令启动仿真器时，可以正常启动GUI界面，但无法正常打开文件，从报错信息推测是渲染引擎的问题。目前暂未确定出错原因。

+ **解决方案**：指定渲染引擎启动

```bash
gz sim -v 4 --render-engine ogre
```


---
## 画面卡顿

