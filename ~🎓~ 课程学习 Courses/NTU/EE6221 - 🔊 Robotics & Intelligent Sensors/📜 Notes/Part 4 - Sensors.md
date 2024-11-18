Sensors play an important role in robots and control system providing feedback information. 

+ [[#Sensors Overview]]
	+ [[#Internal and External Sensors]]
	+ [[#Active and Passive Sensors]]
	+ [[#Sensor Characteristics]]
	+ [[#Multi-Sensor Integration and Fusion]]
+ [[#Vision System Basics]]
	+ [[#Pinhole Camera Model]]
	+ [[#Color Spaces]]
	+ [[#Image Convolution]]
+ [[#Structure & Pose Estimation]]
+ [[#Vision-based Control and Estimation]]
+ [[#Kalman Filter and Sensor Integration]]


---
## Sensors Overview



### Internal and External Sensors

If the robot system is considered a black box model, all the robot sensors can be categorized into two types based on their observing target.

+ Proprioceptive (Internal) - Looking inside the black box, observing the internal states
+ Exteroceptive (External) - Looking outside the black box, observing the environment
+ Exproprioceptive

### Active and Passive Sensors



### Sensor Characteristics 


### Multi-Sensor Integration and Fusion



### List of Common Sensors


---
## Vision System Basics

+ **Goal** - Derive the camera coordinate mapping model

Vision systems use visual data as a part of the feedback signal to ensure stability of the system. Important components of a vision systems include the cameras (sensors) and the processing algorithms.

### Pinhole Camera Model

Pinhole Model of the camera basically explains the mechanics of a camera based on the rules of geometrical optics. The mechanics can be represented by the pinhole calibration equation, which maps a original point from the world frame to the corresponding image frame.

+ Pinhole Calibration Equation
$$\begin{bmatrix}u\\v\\1\end{bmatrix}=\begin{bmatrix}\sigma_x&-\sigma_x\tan\alpha&u_0\\0 &\sigma_y\sec\alpha&v_0\\0&0&1\end{bmatrix}\begin{bmatrix}\frac{f}{z}&0&0&0\\0&\frac{f}{z}&0&0\\0&0&\frac{f}{z}&0\end{bmatrix}\begin{bmatrix}R_{3\times3}&T_{3\times1}\\0_{1\times3}&1\end{bmatrix}\begin{bmatrix}x_w\\y_w\\z_w\\1\end{bmatrix}$$
Four different coordinate frames used in the model. As the mapping involves coordinate transform between frames, homogeneous form of points are used. 

+ **World frame** (3D) - the fixed reference frame for the whole system
+ **Camera-centered frame** (3D) - origin at the camera pinhole
+ **Image Projection frame** (2D) - origin at the center of image surface
+ **Image frame** (2D) - the pixel coordinate of the point projected on the image surface, origin at the left-top corner

The process of pinhole capturing a image can be summerized into three coordinate transforms, which is represented respectively by the three matrix.

1. **Regular 3D Coordinate Transform** - World frame --> Camera-centered frame
2. **3D-to-2D Project Transform** - Camera-centered frame --> Image Projection frame
3. **Rotation and Pixelization** - Image Projection frame --> Image frame (Pixel)


### Color Spaces


### Image Convolution



---
## Structure & Pose Estimation

+ **Goal** - Estimate structure of a 3D object and robot pose from sensor data

A major drawback of vision sensing is the loss of depth (distance) information because of the 
geometric similar phenomena during projection. 

However, the depth information can be regained by comparing a series of reference points in images.

Assume the 




### Essential Matrix and 8-point Algorithm

+ Essential Matrix
$$E=[x]_\times R$$


### Homography Matrix and 4-point Algorithm

+ Homography Matrix
$$H=R+\frac{x}{d^*}n^{*T}$$
+ Ratio of Depth
$$\alpha_j=\frac{z_j^*}{z_j}$$

## Stereo vision



### Optical Flow


---
## Vision-based Control and Estimation



### Position Based Visual Servoing (PBVS)



### Image Based Visual Servoing (IBVS)


---
## Kalman Filter and Sensor Integration

+ **Goal** - Integrate the observation of different sensors and obtain the optimal measurement

Kalman Filter is a state estimator which is widely used in sensor intergration. The mechanics 
 
