> 电路工作的本质是物理，电路分析的本质是数学

+ Wikipedia - [Network Analysis](https://en.wikipedia.org/wiki/Network_analysis_(electrical_circuits))

电路分析本质上是对理想的线性网络模型进行数学分析。

线性网络指的是由线性元件组成的电路网络结构，非线性元件（晶体管、二极管、非线性电阻等）组成的电路也常用线性网络拟合以简化分析

---
## 线性元件 Linear Component

+ 

典型的线性元件如下，它们本质上是现实中对应元件的理想数学模型，从数学形式上理解，它们是表示电流电压之间关系的函数。

| 元件 Component           |          时域模型           |           频域模型            | 复频域模型 |     |
| :--------------------- | :---------------------: | :-----------------------: | ----- | --- |
| 电压源 Voltage Source     |         $u(t)$          |             /             |       |     |
| 电流源 Current Source     |         $i(t)$          |             /             |       |     |
| 受控电源 Controlled Source |                         |                           |       |     |
| 电阻 Resistor            |     $$u(t)=Ri(t)$$      |         $$U=RI$$          |       |     |
| 电容 Capacitor           | $$i(t)=C\frac{dv}{dt}$$ | $$U=\frac{I}{j\omega C}$$ |       |     |
| 电感 Inductor            | $$u(t)=L\frac{di}{dt}$$ |     $$U=Ij\omega L$$      |       |     |

---
## 阻抗与导纳 Impedance and Admittance




---
## 阻抗变换 Impedance Transform


