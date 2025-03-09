+ Pypi官网：[Pypi](https://pypi.org/)
+ Pip文档：[Pip Documentation](https://pip.pypa.io/en/stable/)

Pypi（Python Package Index）是Python官方的第三方库仓库，它提供的包下载工具为Pip，可用于直接下载Pypi上提供的所有库。Python自带Pip，不需要另外下载。

Pypi上的库是最全的

---
## 下载

默认下载最新版本

```bash
pip  install  numpy
```

指定版本下载

```bash
pip  install  numpy==1.20.0
```

指定源、版本下载

```bash
pip  --default-timeout=100  install  numpy==1.20.0  -i https://pypi.tuna.tsinghua.edu.cn/simple
```

---
## 版本

查看包的所有可用版本

```bash
pip  index  versions  numpy
```

查看已下载的包的详细信息（包括版本）

```bash
pip  show  numpy
```

---
## 