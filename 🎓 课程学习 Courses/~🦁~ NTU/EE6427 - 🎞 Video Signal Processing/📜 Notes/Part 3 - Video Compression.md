+ **Goal** - Compress video to make it smaller for storage or transmission
+ **Approach** - 

+ Foundamental Concept of Video Compression
	+ [[#Intraframe vs Interframe]]
	+ [[#Chroma Subsampling]]
	+ [[#Motion Estimation & Compensation]]
		+ [[#Type of Frames]]
		+ [[#Estimation Process]]
		+ [[#Searching Methods]]
	+ [[#Compressed Video Data Structure]]
+ Features of Video Compression Standards
	+ [[#Video Compression Standard Overview]]
	+ MPEG-1 - [[#Inter-coded Frames]]
	+ MPEG-2 - [[#Scalable Coding]]
	+ MPEG-4 - [[#Object-Based Coding]]
	+ H.264 (MPEG-4 Part 10) :
		+ [[#Sub-pixel accuracy of motion compensation]]
		+ [[#Integer Transform]]
		+ [[#Intra Coding]]

### Reference

+ [Macroblock Filter](https://blog.ampedsoftware.com/2016/03/08/understanding-the-macroblocks-filter)
+ [Chroma subsampling](https://en.wikipedia.org/wiki/Chroma_subsampling)

---
## Intraframe vs Interframe

+ **Intraframe compression** -  the compression methods designed for images can be used on single frame of a video

+ **Interframe compression** - Compression methods based on multi-frames. Make use of temporal redundancy.

| Compression Type | Dimension |
| ---------------- | --------- |
| Interframe       | Temporal  |
| Intraframe       | Spatial   |

---
## Chroma Subsampling

+ **Make use of** - Spatial Redundancy & Psycho-visual Color Redundancy

Chroma Subsampling is a intraframe compression method, it intends to compress the $C_b$ and $C_r$ components of an intra frame, reducing the required bandwidth for video transmission. 

![[Pasted image 20241025164334.png]]

Chroma Subsampling is usually applied to a region of $2\times4$ pixels. The sampling strategy has two steps

1. Sample the **value** of pixels in the first row
2. Sample the **difference** of pixels between the first and the second row

The sampling scheme is denoted as a three-part ratio $J:a:b$

+ $J$ - the number of pixels in each **row**
+ $a$ - the number of first row value sample
+ $b$ - the number of first and second row **difference** sample


---
## Motion Estimation & Compensation

+ **Type** - Interframe compression
+ **Make use of** - Temporal Redundancy

The existence of temporal redundancy implies that adjacent frames of a video are similar. Inspired by this, it's possible to only record the difference between nearby frames.

### Type of Frames

There are three types of frames in a group of picture (GOP)

 + **I-frame** (Intra-coded) - Completely independent frame, not temporally compressed
 + **P-frame** (Predictive-coded) - Code with prediction from the last **I-frame** or **P-frame**
 + **B-frame** (Bidirectional-coded) - Code with prediction from the adjacent **I-frame** or **P-frame**

![[Pasted image 20241024134914.png]]
Because of the dependency chain:

+ A P-frame can only be decoded after its predecessor P- or I-frame is decoded.
+ A B-frame can only be decoded after its adjacent P- or I-frame at both directions are decoded.

### Estimation Process

When encoding a P-frame or B-frame (called target frame), for every macroblocks, we must find its corresponding macroblock in the reference frame.

Actually, finding a completely identical macroblock is difficult. We just need to find a **similar** one with a acceptable low error nearby

Once the reference macroblock is found, the following will be encoded.

+ **Motion Vector** - pointing from the location of target macroblock to its reference macroblock
+ **Error** - record the difference between the target and its corresponding reference macroblock

![[Pasted image 20241026170602.png]]

If no reference macroblock is found, the target macroblock will be encoded independently.

### Searching Methods

Searching method determines the searching strategy for the corresponding reference macroblock. All the searching algorithm besides Full Search has the following characteristics

+ It can **not** guarantee finding the corresponding macroblock even there exists one.
+ It does **not** cover every macroblocks in the reference picture. 

| Methods        | Efficiency | Accuracy  |
| -------------- | ---------- | --------- |
| Full Search    | very low   | very high |
| Three Step     | very high  | very low  |
| 2D Logarithmic | high       | low       |
| Hierarchical   |            |           |

+ Three Step Search - 


+ 2D Logarithmic Search


+ Hierarchical Search

---
## Compressed Video Data Structure

+ **Hierarchy** - Video >> Group of Pictures (GoP) >> Picture (Frame) >> Slice >> Macroblock >> Block >> Encoded Coeffcient 

A compressed video can be divided into smaller substructures for processing simplicity.

1. **Group of Pictures (GoP)** - A subgroup of frames, usually begin and end with I-frames which is encoded independently and serves as the reference for interframe encoding in the GoP

2. Picture (Frame) - The unit of a video

3. Slice - A subgroup of continuous pixels in a frame

4. **Macroblock** - The smallest unit of typical video processing algorithm

5. Block - A subset of macroblock

---
## Video Compression Standard Overview

MPEG and H.29X are two of the most widely used standard for compression.

![[Pasted image 20240926154910.png]]

![[Pasted image 20241024121533.png]]

### Inter-coded Frames

 + Standard - MPEG-1

MPEG-1 is the first standard to include both P-frame and B-frame encoding.




### Scalable Coding

 + Standard - MPEG-2

Scalable Coding brings great flexibility to the video compression process by dividing the process into different layers. The base layer and enhencement layer can be independently encoded and transmitted.

+ Base layer - Low quality
+ Enhencement layer - Improved quality

### Object-Based Coding

 + Standard - MPEG-4



### Sub-pixel accuracy of motion compensation

+ Standard - H.264 (MPEG-4 Part 10)
+ Max Precision - $1/4$ Pixel

Sub-pixel precision of H.264 can reach $1/4$ pixel and is achieved by pixel value interpolation.



#### Integer Transform

+ Standard - H.264 (MPEG-4 Part 10)



#### Intra Coding

+ Standard - H.264 (MPEG-4 Part 10)
+ Make use of - Spatial Redundancy

Intra Coding is a intra encoding and compression method based on picture spatial redundancy. Since the value of nearby 