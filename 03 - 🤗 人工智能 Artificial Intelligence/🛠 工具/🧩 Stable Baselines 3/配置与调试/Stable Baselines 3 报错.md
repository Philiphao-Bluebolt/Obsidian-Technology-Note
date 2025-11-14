和所有的Python库一样，Stable Baselines 3也会因为依赖项版本问题报错

[[#MuJoCo：`MjData`缺少`solver_iter`属性]]


---
## MuJoCo：`MjData`缺少`solver_iter`属性

+ 问题反馈：[\[Bug Report\] Incompatible with mujoco 3.0.0](https://github.com/Farama-Foundation/Gymnasium/issues/749)

```bash
AttributeError: 'mujoco._structs.MjData' object has no attribute 'solver_iter'
```

这个报错在使用MuJoCo环境时可能会出现；这是因为Python的`mujoco`接口库在3.0.0版本以上将属性`solver_iter`改为了`solver_niter`，而`gymnasium`没有跟进这个改动

解决方案：将`mujoco`接口库版本回退到3.0.0以下

```bash
pip  install  mujoco==2.3.7
```

（2024/04/29）

---
