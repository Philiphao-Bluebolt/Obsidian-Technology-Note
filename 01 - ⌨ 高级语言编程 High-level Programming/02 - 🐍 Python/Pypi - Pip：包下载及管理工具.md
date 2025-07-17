

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