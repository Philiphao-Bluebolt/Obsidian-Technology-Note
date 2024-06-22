+ Youtube：[Understanding framerate independence and deltatime](https://www.youtube.com/watch?v=rWtfClpWSb8&ab_channel=ClearCode)

电子游戏的画面渲染由一个循环体控制，因此在代码中，物体运行的速度不是以时间单位衡量，而是**以帧为单位衡量**（像素/帧）

比如说，玩家的移动速度可以定义为10px/f（10像素/帧）

但这样定义的话，玩家的移动速度和帧率相关，低帧率时移动得很慢，高帧率时移动得很快，导致游戏无法正常游玩。

因此需要引入`dt`（Delta Time）

---
## Delta Time

Delta Time指的是上一帧到当前帧的实际时间间隔，也就是瞬时渲染周期。

这是一个速度调节因子，在所有控制速度移动的运算语句中乘上`dt`，高帧率时降低帧速度，低帧率时提高帧速度，从而使物体运动速度与时间而不是帧率相关。