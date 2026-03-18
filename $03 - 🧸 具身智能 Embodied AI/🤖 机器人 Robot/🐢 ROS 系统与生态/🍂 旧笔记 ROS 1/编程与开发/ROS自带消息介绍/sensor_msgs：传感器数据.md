+ 官方文档：[http://wiki.ros.org/sensor_msgs](http://wiki.ros.org/sensor_msgs)

`sensor_msgs`一般作为传感器采集的原始数据的载体。

无人机传感器的数据采集和处理详见[[2. 无人机传感器]]

---
## `Image`：图像

`sensor_msgs/Image`一般是相机等视觉传感器的输出图像，像素值线性存放在`data`数组中，其他几个参数说明图像的尺寸和数据格式。

```msg
Header header

uint32 height
uint32 width

string encoding
uint8 is_bigendian
uint32 step

uint8[] data
```

+ `data`：存放像素值的数组，每个元素一个字节（8比特）

+ `height`：像素行数
+ `width`：像素列数

+ `encoding` ：图像的编码格式名称，常见格式见下方补充
+ `is_bigendian`：是否高位在前，若为1，数组先存高位字节再存低位字节

举例，如果某个`mono16`格式的像素取值为14626，即二进制无符号数的00‭11 1001 0010 0010，‬如果是**低位在前**，则前一个字节是0010 0010，后一个字节是00‭11 1001

+ `step`：一行的字节数，设计这个参数是为了方便访问单个像素点

### 计算像素点序号

下面展示了如何计算像素点在`data`数组中的序号；其中`pixelSize`指的是存放一个像素点的**字节数**，取决于编码格式`encoding`的**通道数**和**精度位数**（记住，行列数`row`和`column`从0开始）

```cpp
pixelIndex = row * step + column * pixelSize
```

### 补充：`encoding`常见格式

+ `mono8`或`8UC1`：8位灰度图，单通道，`pixelSize = 1`
+ `mono16`或`16UC1`：16位灰度图，单通道，`pixelSize = 2`
+ `bgr8`：8位彩色图，三通道，储存顺序蓝绿红，`pixelSize = 3`

`Image`消息支持OpenCV、Bayer等多种图像格式，完整的格式定义参见文件

```bash
gedit  /opt/ros/noetic/include/sensor_msgs/image_encodings.h
```


---