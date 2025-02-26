+ **Goal** - Reduce the bits used to represent a certain image
+ **Premise** - Ubiquitous existence of redundancy in images and videos
+ **How to do** - Transform --> Quantize --> Encode 

![[Pasted image 20240822184002.png]]

+ [[#Redundancy]]
+ [[#Compression Metrics]]
	+ [[#Entropy of Information Source]]
	+ [[#Compression Ratio]]
+ [[#Compression Loss]]
	+ [[#Lossy vs Lossless]]
	+ [[#Distortion Metrics]]
+ [[#Huffman Coding]]
	+ [[#Huffman Tree]]
+ [[#2-D Discrete Cosine Transform (2-D DCT)]]
	+ [[#Definition]]
	+ [[#Matrix Implementation]]
	+ [[#Inverse 2-D DCT]]
	+ [[#Base Functions]]
	+ [[#Manual Calculation Tips]]
	+ [[#2D-DCT functions in Programming]]
+ [[#JPEG Baseline Compression]]
	+ [[#Quantization]]
	+ [[#Vectoring]]
	+ [[#Differential Encoding]]
	+ [[#Run-Length Encoding]]

---
## Redundancy

Redundancy refers to the usage of too many bits to represent a certain information than necessity. It's the existence of redundancy in digital images and videos that makes compression possible.

+ Statistical Redundancy (Objective)
	+ **Spatial** - Adjacent pixels in a image have similar values
	+ **Temporal** - Adjacent frames of a video are similar (Interframe redundancy)
	+ **Coding** - Use too many bits to represent a information
+ Psycho-visual Redundancy (Subjective) 
	+ **Frequency Masking** - reduce high frequency components 
	+ **Color Masking** - reduce color components

Humans are more sensitive to low frequency components and luminance components of a image.


---
## Compression Metrics

Entropy of Information Source and Compression Ratio are important metrics describing a compression process.

### Entropy of Information Source

+ Wiki - [Entropy (information theory)](https://en.wikipedia.org/wiki/Entropy_(information_theory))

Entropy quantifies the level of uncertainty associated with the variable's potential states. It also measures **at least** how much imformation must be used to perfectly describe every state of the random variable.

+ Definition - Assume there is a information Source $S$ that has $n$ possible states $\{s_1, s_2, ..., s_n\}$ and the probability of each state $s_i$ appearing is denoted as $p_i$. Then the entropy
$$\begin{align}\eta=H(s)&=\sum_{i=1}^n p_i\log_2 \frac{1}{p_i}\\&=-\sum_{i=1}^n \log_2 {p_i}^{p_i} \end{align}$$
### Compression Ratio

Compression Ratio describes the efficiency of compression. As the numerator is bit before compression, the metrics would be larger than 1.
$$CR=\frac{B_i}{B_o}$$
$B_i$ - Bits of input data (before compression)
$B_o$ - Bits of output data (after compression)


---
## Compression Loss

Some compression methods can result in loss of information. Generally, lossy compression achieves larger compression ratio. 

### Lossy vs Lossless

| Type     | Usage          | Can rebuild original image |
| -------- | -------------- | :------------------------: |
| Lossy    | General Media  |             N              |
| Lossless | Important Data |             Y              |

### Distortion Metrics

Distortion Metrics measures the loss in information in image compression.

+ Mean Square Error (MSE)
+ Signal to Noise Ratio (SNR)
+ Peak Signal to Noise Ratio (PSNR)


---
## Huffman Coding

+ **Goal** - Using less bits to represent a sequence
+ **Frequency Based** - Shorter code for higher frequency patterns
+ Method - Use a **binary tree** for assigning codes

Huffman Coding is one of the frequency based coding method, it uses shorter code for high frequency patterns or states, reducing the average length of the coding sequence.

For example, here's a string with 25 characters that need to be coded into bits.
$$ABCDCDDBBDDCDADDBBBCBBBBC$$

Traditionally, 2 bits will be used to encode four states respectly, the total length of the encoded sequence would be 50 bits.

### Huffman Tree

+ Calculate the frequency of each character in the string

| Character ($s_i$)     | A    | B   | C   | D    |
| --------------------- | ---- | --- | --- | ---- |
| **Frequency ($p_i$)** | 0.08 | 0.4 | 0.2 | 0.32 |

+ Draw the huffman tree. 

1. Pick out the two least frequent states $A, C$ from the list $[A,B,C,D]$ and assign them to the same parent node $P_{AC}$, the frequency of $P_{AC}$ is the sum of $A,C$
2. Put parent node $P_{AC}$ back to the choice list - $[P_{AC},B,D]$
3. Do the same thing as step 1 (Pick out $P_{AC},D$ and assign them to a parent node $P_{ACD}$)
4. Repeat the steps until all the states are assigned.
![[Pasted image 20240905123047.png]]
The average bits for a character is 1.88 bits. Not much lesser than using traditional method, but the difference would be considerable for longer sequence.

| Method         | A   | B   | C   | D   | Bits/Char | 10 Chars  | 100000 Chars |
| -------------- | --- | --- | --- | --- | --------- | --------- | ------------ |
| Binary Coding  | 00  | 01  | 10  | 11  | 2 bits    | 20 bits   | 200000 bits  |
| Huffman Coding | 000 | 1   | 001 | 01  | 1.88 bits | 18.8 bits | 188000 bits  |

---
## 2-D Discrete Cosine Transform (2-D DCT)

+ **Goal** - Seperate low frequency and high frequency coefficients for frequency masking
+ **Function** - Energy Compaction, Redundancy Reduction, Change Prospective
+ Shortage - Inefficient

The 2-D Discrete Cosine Transform is a Fourier-related discrete transform that maps a image to the frequency domain.

### Definition

For a $N\times N$ pixels image $s_{ij}$ , the 2-D DCT is defined by the following expression in which $S_{uv}$ is a pixel value of the output transformed image and $s_{ij}$ is a original pixel
$$S_{uv}=\alpha(u)\alpha(v)\sum_{i=0}^{N-1}\sum_{j=0}^{N-1}s_{ij}\cos\frac{(2i+1)u\pi}{2N}\cos\frac{(2j+1)v\pi}{2N} \quad u,v=0,1,...,N-1$$
The constant $\alpha$ is determined by the value of $u,v$ 
$$\alpha(x)=\begin{cases}\sqrt{\frac{1}{N}}&x=0\\\sqrt{\frac{2}{N}} &x=1,2,...,N-1\end{cases}$$
### Matrix Implementation

For a $N\times N$ pixels image $f(i,j)$ , the matrix form 2-D DCT is defined by the multiplication of $f_(i,j)$ and the DCT-matrix $T$
$$F(u,v)=T\cdot f(i,j)\cdot T^T$$
The DCT-matrix $T$ is defined as
$$T(i,j)=\begin{cases} \sqrt{\frac{1}{N}} & i=0\\\ \sqrt{\frac{2}{N}}\cdot\cos\frac{(2j+1)\cdot i\pi}{2N} & i>0\end{cases} \quad \quad i,j=0,1,...,N-1$$

### Inverse 2-D DCT

The calculation of 2-D IDCT can much easier in matrix form
$$f(i,j)=T^T\cdot F(u,v)\cdot T$$
Notice that DCT-matrix $T$ is invertible and orthogonal
$$T^T=T^{-1}$$

### Base Functions

+ **What is it?** - Intuitively, the **linear combination** of base functions with transformed image $F(u, v)$ as coefficients is the original image.

![[Pasted image 20240912172437.png]]

### Manual Calculation Tips

When doing manually, 2D-DCT can be seperated into two 1D-DCT to simplify calculation. The first 1D-DCT is row-wise and the second one is column-wise.
$$S_{k}=\alpha(k)\sum_{n=0}^{N-1}s_{n}\cos\frac{(2n+1)k\pi}{2N} \quad k=0,1,...,N-1$$
$$\alpha(k)=\begin{cases}\sqrt{\frac{1}{N}}&k=0\\\sqrt{\frac{2}{N}} &k=1,2,...,N-1\end{cases}$$
In the equation, $S_k$ is a pixel after transformation and $s_n$ is a original pixel. $N$ is the number of pixels in a row or a column.

### 2D-DCT functions in Programming

+ Matlab - `dct2()`
+ OpenCV - `dct()`

---
## JPEG Baseline Compression

+ **Input** - YCbCr Image
+ **Output** - Compressed data
+ **Stages** - 8x8 Partition --> 2-D DCT --> Quantization --> Vectoring --> DE, RLE --> Entropy Encoding

![[Pasted image 20240912171349.png]]

### Quantization

+ **Goal**
	+ **Discretization** - Continuous DCT coefficient --> Discrete coefficient
	+ **Frequency Masking** - Higher quantization coefficient for high frequency coefficient
	+ **Color Masking** - Higher quantization coefficient for Cb, Cr channels
+ **Prerequisite** - Frequency domain power 
+ **Side Effect** - Information loss

The process of quantization is to divide each element in the DCT matrix by a specially designed quantization matrix. The quantization matrix should be designed with greater elements at the right-down side, aiming to compress more on the high frequency components in the DCT matrix.

For colored image, the Cb Cr chroma channels should be compressed more fiercely than the Y channel.

### Vectoring 

+ **Goal** - Convert the matrix DCT data to linear vector form, making encoding more easy.
+ **Approach** - Zig-zag Scanning

The zig-zag scanning ensure that:

+ DC component is always the first element of the output vector 
+ AC components are sorted in frequency, highest frequency components located in the back are likely to be zero.

### Differential Encoding

+ **Used on** - DC component
+ **Make use of** - Spatial Redundancy

The DC components of multiple blocks are represented together by a vector recording the difference between DC components of adjacent blocks.

### Run-Length Encoding

+ **Used on** - AC component
+ **Make use of** - the majority of zero value in high frequency components

The AC components of a single block are represented by a vector that record: 

+ Each non-zero component
+ The number of zero between it and the next non-zero component