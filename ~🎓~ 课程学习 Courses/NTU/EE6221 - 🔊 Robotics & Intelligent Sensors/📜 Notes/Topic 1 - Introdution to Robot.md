Robot is an umbrella term for all the automatic machines, but we'll only focuse on **industrial robot arms** in this course for simplicity.

[[#Robot Joints]]


---
## Robot Joints

+ Purpose - Control the **DoF** of the robot, move the end-effector to a certain **position and orientation**

Rigid robot arms can be seen as a tree of joints and links just like the human arms mathematically. The type of joint determines the Gross Work Envelope as well as how will the robot move.

+ By purpose
	+ **Major** Axes - The first three joint axes, control the end-effector's position within the Gross Work Envelope
	+ **Minor** Axes - Remain joint axes, control the end-effector's orientation
+ By motion
	+ **Revolute (R)**
	+ **Prismatic (P)**

**Gross Work Envelope** is the 3D area that the robot's end-effector can reach for, it focuses on the end-effector position.

**Orientation Range** of the end-effector is usually equally important because many tasks require the rotary motion of the end-effector.

---
##