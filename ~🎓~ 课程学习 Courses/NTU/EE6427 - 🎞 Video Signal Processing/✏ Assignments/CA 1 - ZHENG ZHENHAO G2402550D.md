
---
## 1 - Manual 2D-DCT

Compute manually the 2-D DCT of the following image block A using **2-stage decomposition**.
$$A=\begin{bmatrix}10&10&20&20\\10&10&20&20\\0&0&0&0\\0&0&0&0\\\end{bmatrix}$$
The 1D-DCT expression is given by
$$S_{k}=\alpha(k)\sum_{n=0}^{3}s_{n}\cos\frac{(2n+1)k\pi}{8} \quad k=0,1,2,3$$
$$\alpha(k)=\begin{cases}\frac{1}{2}&k=0\\\sqrt{\frac{1}{2}} &k=1,2,...,N-1\end{cases}$$
The row-wise or column-wise 1D-DCT is given by
$$S_0=\frac{1}{2}(s_1+s_2+s_3+s_4)$$
$$S_1=\sqrt{\frac{1}{2}}(s_1\cos\frac{\pi}{8}+s_2\cos\frac{3\pi}{8}+s_3\cos\frac{5\pi}{8}+s_4\cos\frac{7\pi}{8})$$
$$S_2=\sqrt{\frac{1}{2}}(s_1\cos\frac{\pi}{4}+s_2\cos\frac{3\pi}{4}+s_3\cos\frac{5\pi}{4}+s_4\cos\frac{7\pi}{4})$$
$$S_3=\sqrt{\frac{1}{2}}(s_1\cos\frac{3\pi}{8}+s_2\cos\frac{9\pi}{8}+s_3\cos\frac{15\pi}{8}+s_4\cos\frac{21\pi}{8})$$
The image block after applying 1D-DCT on the rows
$$\begin{bmatrix}30&-9.24&0&3.83\\30&-9.24&0&3.83\\0&0&0&0\\0&0&0&0\end{bmatrix}$$
The image block after applying 1D-DCT on the columns
$$\begin{bmatrix}30&-9.24&0&3.83\\27.72&-8.54&0&3.54\\0&0&0&0\\-11.48&3.54&0&-1.46\end{bmatrix}$$

