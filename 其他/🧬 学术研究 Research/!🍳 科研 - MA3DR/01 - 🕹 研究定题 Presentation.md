+ **链接** - [BioRAI](https://vlislab22.github.io/vlislab/) | 

**Material-aware** 3D Reconstruction is a potential and interesting topic, however it's just a concept rather than a **concrete** and **worthy** problem. There're two ways to transform the concept into a problem, optimization and exploitation.

As suggested by Professor Wen, 方法总比困难多, thus it's not easy to optimize the current methods since they're already polished carefully by the inventors. It's more feasible solve a problem using the current methods.

+ ❌ **Difficult** - Existing Method 🛠 --> Improved Method 🍀🛠
+  **Simplier** - Existing Method 🛠 --> Unsolved Problem 🔐 --> Solved Problem 🔓

+ **Preparation**
	+ [Vision-Tactile-based Material Panoptic Reconstruction](#Vision-Tactile-based%20Material%20Panoptic%20Reconstruction)
	+ [Presentation](#Presentation)
	+ [Q&A](#Q&A)
+ **Possible Problems**
	+ 🏖️ [Panoptic Reconstruction](#Panoptic%20Reconstruction)
	+ 🦾 [Contact Rich Manipulation](#Contact%20Rich%20Manipulation)
	+ 🗺️ [Simutaneously Localization and Mapping](#Simutaneously%20Localization%20and%20Mapping)
	+ 🌑 [Low-light Scene Reconstruction](#Low-light%20Scene%20Reconstruction)


---
## Vision-Tactile-based Material Panoptic Reconstruction

Contact-rich manipulation is a cutting-edge topic in robotics. It comprises of tasks envolving frequent contacts with the environment and thus, requiring an accurate control of force. For example, changing the light bulb is a contact-rich task in which the grasping force output should not be too large or small, otherwise, the light bulb could break or slip within the grabber.

The material recognition task has been widely researched. However, most existing methods are  vision-based, making them difficult to recognize the material of painted or textureless objects. Those drawbacks can be eliminated by integrating the tactile modal data since tactile sensing has a better perception of the friction, stiffness, thermal conductivity and vibration.




### Difficulties

> **Nonstandardized Tactile Sensors**

Robot tactile sensors are currently under-researched and rarely used in the robotic industry owing to their lack of robustness and continuity. As a result, there's **no** standard or consensus regulating the design of tactile sensors, not to mention the software and data format. They can vary in shapes, functions or even sensing principles. If you are not designing your own sensor, detailed research on the marketable tactile sensors before purchasing is highly recommended. The wrong choice of sensor would greatly slow down the experiment process. 



### Methodology

+ Reconstruction backbone - VGGT or 3DGS
+ Panoptic Model - 
+ Tactile Sensing Fusion - 

### Thoughts

I personally think the title unconcrete and not problem-focusing enough. Actually, since the title is inspired by robot contact-rich manipulation tasks, why not just set those tasks as the paper goals? It'll natually privide some evaluation baselines if I do it. 

I try to search for some robot manipulation tasks that may be benefited from the material panoptic reconstruction. For example:

+ **Indoor (Household-based) scene manipulation** - seems too complex and the evaluation might involve lots of other robotics task such as locomotion.

+ **Flexible Object Manipulation** - handles deformable and flexible object such as clothes, handbag and balloons, which is a challenge in manipulation.

+ ****


---
## Presentation

+ Decent Outfit
+ Print my CV

+ How to persuade the audience to believe that the research topic is worthy
+ How to persuade the audience to believe that I can complete this research 

---
## Q&A

> **What is your research problem?** 

To develop a enhanced panoptic reconstruction method that is capable of accurately recognizing material of the objects in the scene. In a nutshell, I want to combine panoptic reconstruction and material recognition, providing a 

> **If your goal is to improve contact-rich manipulation, why bother reconstructing the scene rather than just using 2D images for localization?**



> **Why do you use visual-tactile sensing rather than the mainstream visual sensing since material recognition can be simply achieved by visual algorithms?**


> **Why don't you use VTL-based methods**


---
## Panoptic Reconstruction

Panoptic Reconstruction aims to identify and distinguish different **instances** in the same object class while reconstructing the scene geometry. In a nutshell, Panoptics = Semantics + Instance Segmentation.

Challenge of Panoptic Reconstruction includes

+ **Stuff and Thing** - difficult to draw the line between uncountable stuffs (wall, floor) and countable things (furniture, tableware, equipment)
+ **Instance Tracking** - difficult to track an instance in different view due to occlusion and confusion



### Problem - Definition and Value




### Current Methods - Pros and Cons




### My Method - Fundamentals, Pros and Cons




### My Method -  and Optimization




---
## Contact Rich Manipulation


### Problem - Definition and Value




### Current Methods - Pros and Cons




### My Method - Fundamentals, Pros and Cons




### My Method -  and Optimization





---
## Simutaneously Localization and Mapping


### Problem - Definition and Value

SLAM is a crucial problem in Robotics since it's the bridge between robot perception and planning. Its target is to estimate a map $m_{t+1}$ of the surrounding environment and the robot's location $x_{t+1}$ within the map simutaneously **in real time**, based on all the past control input $u_{t}$ and sensor observations $o_{t+1}$
$$P(m_{t+1},x_{t+1}|o_{t+1},u_t)$$


### Current Methods - Pros and Cons




### My Method - Fundamentals, Pros and Cons




### My Method -  and Optimization



---
## Low-light Scene Reconstruction



### Problem - Definition and Value




### Current Methods - Pros and Cons




### My Method - Fundamentals, Pros and Cons




### My Method -  and Optimization




---
## 参考文献

+ [VGGT](💐%20VGGT%20-%20Visual%20Geometry%20Grounded%20Transformer.md) -（Best Paper 2025）截至2025年效果最好的3D重建技术，Transformer架构
+ 