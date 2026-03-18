
---
## GOP Compression

1. Which type of frames has the largest and smallest compression ratio? I-frame, P-frame or B-frame
2. How to choose a suitable GOP size?

I-frame has the smallest compression ratio as it doesn't make use of temporal redundancy at all. B-frame has the largest compression ratio because it uses motion estimation from two directions.

If the GOP size is too small, then the proportion of I-frame will be high, resulting to a low total compression ratio. If it's too large, some of the B-frames will be too lossy as the dependency hierarchy becomes deep.

---
## MPEG-1

1. What is the purpose of chroma subsampling?
2. Use a flowchart to describe how P-frame are encoded.
3. Explain the role of entropy encoding in the P-frame encoding process.


Chorma subsampling is invented as a stage of MPEG-1 video compression, which is to reduce the required bandwidth for video transmission. It actually makes use of the color redundancy, which is a psycho-visual effect of human visual system. Humans are more sensitive to the brightness of a image rather than its color component so it's acceptable to remove some of the color information from the video frames. 



---
## MPEG-2 Scalability

+ How can MPEG-2 scalability be used in networks with variable bitrate channels?




---
## H.264 Motion Compensation



---
## H.264 Intra Coding






---
## H.264 Integer Transform in P-frame Encoding

