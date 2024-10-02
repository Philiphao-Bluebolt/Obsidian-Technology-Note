+ **Goal** - Compress video to make it smaller for storage or transmission
+ **Approach** - 

+ [[#Intraframe vs Interframe]]
+ [[#Video Data Structure]]
+ [[#Motion Estimation & Compensation]]
	+ [[#Type of Frames]]
	+ [[#Estimation Methods]]
+ [[#History of Video Compression Standard]]

### Reference

+ [Macroblock Filter](https://blog.ampedsoftware.com/2016/03/08/understanding-the-macroblocks-filter)

---
## Intraframe vs Interframe

+ **Intraframe compression** -  the compression methods designed for images can be used on single frame of a video

+ **Interframe compression** - Compression methods based on multi-frames. Make use of temporal redundancy.

| Compression Type | Dimension |
| ---------------- | --------- |
| Interframe       | Temporal  |
| Intraframe       | Spatial   |

---
## Video Data Structure

+ **Hierarchy** - Video >> Group of Pictures (GoP) >> Picture (Frame) >> Slice >> Macroblock >> Block >> Encoded Coeffcient 




---
## Motion Estimation & Compensation

+ **Type** - Interframe compression
+ **Make use of** - Temporal Redundancy

The existence of temporal redundancy implies that adjacent frames of a video are similar. Inspired by this, it's possible to only record the difference between nearby frames.

### Type of Frames

There are three types of frames 



### Estimation Methods


---
## History of Video Compression Standard

MPEG and H.29X are two of the most widely used standard for compression.

![[Pasted image 20240926154910.png]]






---
## Scalable Coding



---
## Object-based Coding