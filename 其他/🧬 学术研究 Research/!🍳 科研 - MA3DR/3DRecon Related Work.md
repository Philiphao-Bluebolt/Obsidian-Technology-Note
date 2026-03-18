
+ [Introduction](#Introduction)
+ [Literature Review](#Literature%20Review)

---
## Introduction

Robotic perception, especially the exteroceptive sensing, are greatly bio-inspired by the perception system of human beings and other animals. Robots rely on visual sensors such as cameras and lidars to see, and tactile sensors such as pressure and thermal measure unit to feel. Currently, one of the challeges of robot sensing is to understand the surrounding scenes as precise and efficient as human beings. An accurate recognition of the geometry and material is required for such understanding.

Human recognizes the nearby scenario and objects using a complex biological multi-modal sensing and perception system comprised of the neuron system and several sensory receptors such as the eyes and the four sensory receptors embeddied in the skin. The five senses of human are made up of three physical senses, vision, hearing, touch and two chemical senses, smell and taste. Humans rely more on the physical senses to explore the physical world. 

Visual and tactile information, combining with common sense, are mostly used for recognition. In most cases, when someone comes across an object, vision is the first sense to aware the object since it's capable of collecting geometry and depth information of the thing in a distance, followed by touch, which captures more comprehensive signals such as friction, pressure and thermal properties. Such exploration can be adopted by robot, enhancing its capability to understand the physical world. Although tactile sensing, as stated in [Hutmacher's](#^f5f7d0) work, tactile and other sensing modals only get little interest in academia compared with vision.

While operating specific tasks, it's necessary that the robots aware of the real-life location of itself and the surrounding objects, which is known as the SLAM (Simutanously Localization and Mapping) problem. Researchers had found several methods for this problem, for example [ORB-SLAM3](#^3164a4), [F-LOAM](#^e91692) and VINS-Fusion. However, most of those traditional SLAM algorithms have a low mapping resolution and are not capable of object and material recognition. With a increasing demand of agile locomotion and dexterous manipulation in robotics, a more detailed map is required for planning and decision making. Such map can be obtained using 3D Reconstruction.

3D Reconstruction is the process of generating 3D representative of a real-world scene or object in computer based on input 2D images of the captured thing. Its application includes historical site reservation and medical examination. Since 3D Reconstruction is capable of remodeling a photorealistic representation of a scenario, their integration with the preception system can offer a clearer environmental understanding for robots.

---
## Literature Review

The proposed multimodal robot perception strategy involves three topics. 

+ **3D Reconstruction** aims to generate a map representing the surroundings, thus prividing the robot with a more comprehensive understanding of the nearby environment. 

+ **Tactile System** is integrated with the vision system to reduce the modeling error of the 3D geometry and provide material information for better interaction with the environment.

+ **Material-aware 3D Reconstruction** is a variety of 3D reconstruction that is capable of recongizing and rebuilding both geometry and material of the target object or scenario. 

### I. 3D Reconstruction

Currently, most of the state of the art 3D reconstruction methods are based on machine learning. Two of the most popular methods are NeRF and 3DGS. They both intake a series of RGB images and the corresponding poses. The output is a radiance field for the NeRF and a set of point clouds for 3DGS.

The two types of 3D models representation are introduced in the review by [Linglong Zhou et al.](#^8ff9d0)  The explicit forms, including voxel, point cloud and mesh, are efficient and straightforward but have limited resolution. The implicit forms, including implicit surfaces, Signed Distance Function and Radiance Field, offer advantages in saving storage space but is usually computational expensive to explicitize. NeRF uses radiance field for representation and 3DGS uses 3D Gaussian Functions, which are both implicit.

In the review by [Hanry Ham et al.](#^063777), visual 3D Reconstruction methods are classified into three groups based on their required input. The three categories are single image, stereo image and others, such as time of flight and structured light. Both NeRF and 3DGS requires only a set of single RGB images and the poses without depth information, which greatly enhances their applications.

NeRF is invented by [Ben Mildenhall et al.](#^0dc801) in 2020. It remodels a 3D scene using a neural network trained by a series of images of the scene captured from different angle. Once trained, the network is capable of generating a radiance field representation of the scene and rendering the scene from arbitrary viewing angle in a photorealistic quality. However, the rendering is computationally expensive and requires a large number of training images. Some improved version such as [Mip-NeRF](#^58c7e0) and [Instant-NGP](#^26ac9c) were proposed to reduce the rendering time.

3DGS is invented by [Bernhard Kerbl et al.](#^02828b) in 2022. It uses a set of 3D Gaussian functions (ellipsoids) to represent a scene and renders the scene using splatting algorithms. Each of the Gaussian functions is defined by the following parameters: position, covariance, color, opacity and other view-dependent features. The training of 3DGS exploits a supervised learning scheme, optimizing the parameters of the Gaussian functions by minimizing the difference between the rendered 2D images and the original dataset images. Compared with NeRF, 3DGS requires less time to render and capable of real-time rendering, making it useful in robotics. [Milena T. Bagdasarian et al.](#^0eab26) runs a website 3dgs.zip tracking and evaluating all the 3DGS-based algorithms.

### II. Tactile System

Tactile sensing system consists of two parts: hardware and software. The hardware part involves the design of tactile sensors based on physics and material science. Those sensors are capable of detecting thermal,  The software part is related to the design of data processing algorithms and systems. Those algorithms convert raw tactile data, such as vibration, pressure and temperature, for further use. 

According to a review written by [Mahmoud Meribout et al.](#^72f3f1), tactile sensors are categoried into six classes which are capacitive, resistive, piezoresistive, piezoelectric, tribuelectric and optical. 

Visual-based tactile is a novel tactile sensing technology that 


Software part is 


Vision-Tactile Language model 

One of the tactile system task is material recognition. 

[Van Anh Ho; Takahiro Araki et al.](#^d264b9) develops a 


[A. Gómez Eguíluz et al.](#^db87de) fabricated a tactile material recognition system using the SynTouch BioTAC sensor, which is able to capture pressure, compression, vibration and thermal flow. The system collects vibration and thermal data as features of each material. The vibration data is processed using FFT and PCA. The thermal data, combining with the approximated contact area, is used to calculate the thermal conductivity of the material.


### III. Material-aware 3D Reconstruction

Material-awareness refers to the capability of a 3D reconstruction process to recognize and label the material of every voxels or point clouds on the generated 3D map. It allows the robot to  detailedly plan its manipulating and locomotive output. 

According to my survey, the past material-aware 3D reconstruction are achieved by the following methods:

1. **Semantic Segmentation** - Using supervised learning based on textile or material datasets include [MINC](#^e54b9e), KTH-TIPS, and [Flickr Material](#^aa74ea). The segmentation is applied on either the RGB channel of the 2D image or the generated 3D model directly
2. **Visual-Tactile Fusion** - Using visual-based 3D reconstruction to generate the geometry and tactile-based 3D reconstruction to distinguish the material

[Cheng Zhao et al.](#^f35227) combined real-time RGB-D SLAM with a material segmentation network, fusing per-frame material predictions into a dense semantic‑material 3D map. The RGB part of a captured image is input into a ANN (FCN or RNN) for material segmentation, acquiring a material-aware image in which every pixel is marked with a material class. The segmentation neural network is trained by a modified MINC dataset.

[Michael Fischer et al.](#^75b8a3) developed a material click-to-select framework for any renderable 3D asset. When clicking on a specific point on the 3D model, the system generates a series of rendering image from different prospective and uses the SAMa network to segment all the area with the same texture and then backproject the segmentation into point cloud.

Some of the works are exploring the possibility to acquire material information using the integration of visual and tactile sensor. 

[Irving Fang et al.](#^c63028) developed a 3D reconstruction framework called FusionSense. The framework recreationally combines vision and touch when exploring the surroundings. It uses vision to capture the global geometry of the structure and then selectively touch the surface to refine the rebuilt geometry. This method enables a precise reconstruction of objects with reflective or transparent surface and a recognition of object material. 

[Etienne Roberge et al.](#^18667c) 

---
## Reference

> **[Why Is There So Much More Research on Vision Than on Any Other Sensory Modality?](https://www.frontiersin.org/journals/psychology/articles/10.3389/fpsyg.2019.02246/full)** ^f5f7d0

> **[ORB-SLAM3: An Accurate Open-Source Library for Visual, Visual-Inertial and Multi-Map SLAM](https://arxiv.org/abs/2007.11898)**

^3164a4

> **[F-LOAM: Fast LiDAR Odometry And Mapping](https://arxiv.org/abs/2107.00822)**

^e91692

> **[NeRF: Representing Scenes as Neural Radiance Fields for View Synthesis](https://arxiv.org/abs/2003.08934)** ^0dc801

> **[Mip-NeRF: A Multiscale Representation for Anti-Aliasing Neural Radiance Fields](https://arxiv.org/abs/2103.13415)** ^58c7e0

> **[Instant Neural Graphics Primitives with a Multiresolution Hash Encoding](https://arxiv.org/abs/2201.05989)** ^26ac9c

> **[3D Gaussian Splatting for Real-Time Radiance Field Rendering](https://arxiv.org/abs/2308.04079)** ^02828b

> **[A Comprehensive Review of Vision-Based 3D Reconstruction Methods](https://www.mdpi.com/1424-8220/24/7/2314)** ^8ff9d0

> **[Computer Vision Based 3D Reconstruction A Review](https://www.researchgate.net/publication/336887797_Computer_Vision_Based_3D_Reconstruction_A_Review)** ^063777

> **[3DGS.zip: A survey on 3D Gaussian Splatting Compression Method](https://arxiv.org/pdf/2407.09510)** ^0eab26

> **[Tactile sensors: A review](https://www-sciencedirect-com.remotexs.ntu.edu.sg/science/article/pii/S026322412401217X)** ^72f3f1

> **[Experimental Investigation of Surface Identification Ability of a Low-Profile Fabric Tactile Sensor](https://ieeexplore.ieee.org/document/6385538)** ^d264b9

> **[A Multi-modal Approach to Continuous Material Identification through Tactile Sensing](https://arxiv.org/pdf/2311.03090)** ^db87de

> **[Material Recognition in the Wild with the Materials in Context Database](https://arxiv.org/abs/1412.0623)** ^e54b9e

> **[Accuracy and speed of material categorization in real-world images](https://jov.arvojournals.org/article.aspx?articleid=2194073)** ^aa74ea

> **[Simultaneous Material Segmentation and 3D Reconstruction in Industrial Scenarios](https://www.frontiersin.org/journals/robotics-and-ai/articles/10.3389/frobt.2020.00052/full)** ^f35227

> **[SAMa: Material-aware 3D Selection and Segmentation](https://mfischer-ucl.github.io/sama/?utm_source=chatgpt.com)** ^75b8a3

> **[FusionSense: Bridging Common Sense, Vision, and Touch for Robust Sparse-View Reconstruction](https://arxiv.org/html/2410.08282v1?utm_source=chatgpt.com)** ^c63028

> **[StereoTac: a Novel Visuotactile Sensor that Combines Tactile Sensing with 3D Vision](https://arxiv.org/abs/2303.06542)** ^18667c


