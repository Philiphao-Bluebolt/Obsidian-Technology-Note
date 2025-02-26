
+ [[#实用代码]]
	+ [[#基本框架]]
	+ [[#循环高亮连杆]]



---
## 实用代码

### 基本框架

这段代码涵盖了PyBullet的基本运行框架，功能包括启动并链接物理仿真器服务端、导入官方模型资源、设置重力、生成地面、进入仿真循环

```python
import time
import pybullet as p
import pybullet_data

# Environment configuration
physicsClient = p.connect(p.GUI)
p.setAdditionalSearchPath(pybullet_data.getDataPath())
p.setGravity(0, 0, -9.8)

# Load a plane
planePos = [0, 0, 0]
planeOrientation = p.getQuaternionFromEuler([0, 0, 0])
planeID = p.loadURDF("plane.urdf", planePos, planeOrientation)

# Run the simulation
while(1):
    p.stepSimulation()
    time.sleep(1./240.)

p.disconnect()
```

### 获取连杆数量

PyBullet没有提供输出连杆数量的函数，这里取巧一下，数`getVisualShapeData()`的输出元组的长度间接获得连杆数量

```python
def getLinkNums(bodyID):
    return len(p.getVisualShapeData(bodyID))
```


### 循环高亮连杆

默认按`B`键循环高亮指定物体的连杆，运行时暂停仿真

```python
# 运行于仿真循环内
def highlightLinks(bodyID, baseDisplayColor=(1, 0, 1, 0.5), linkDisplayColor=(0.12, 0.56, 1, 0.6), flashPeriod=0.4, triggerKey='b'):

    linkNum = getLinkNums(bodyID)
    color_ori = ()

    # Trigger when the key is pressed
    keys = p.getKeyboardEvents()
    trigger = ord(triggerKey)
    if trigger in keys and keys[trigger] & p.KEY_WAS_TRIGGERED:
        linkNum = getLinkNums(bodyID)

        for i in range(linkNum):
            color_ori = p.getVisualShapeData(bodyID)[i][7]
            p.changeVisualShape(bodyID, linkIndex=i - 1, rgbaColor=linkDisplayColor if i != 0 else baseDisplayColor)
            time.sleep(flashPeriod)
            p.changeVisualShape(bodyID, linkIndex=i - 1, rgbaColor=color_ori)
            
    p.getKeyboardEvents()
```