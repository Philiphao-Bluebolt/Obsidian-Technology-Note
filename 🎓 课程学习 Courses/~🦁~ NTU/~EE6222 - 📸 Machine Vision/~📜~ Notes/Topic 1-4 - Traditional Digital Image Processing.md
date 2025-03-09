The technology of digital image processing has two major targets 

1. **Aesthetics** - beautify the image for human 
2. **Pre-process** - modify the image making it easier for further tasks

Although most image processing tasks are done by AI now, those tasks are completed by hard-coded algorithms traditionally.  

+ **Image Fundemantals**
	+ [[#Image Capture and Perception]]
	+ [[#Color Space]]
	+ [[#Digitization and Resolution]]
+ **Digital Image as a Signal**
	+ [[#Linear Shift Invariant System (LSI)]]
	+ [[#Convolution]]
	+ [[#Fourier Transform]]
	+ [[#Image Sampling]]
+ **Enhancement**
	+ [[#Point Processing]]
	+ [[#Histogram Equalization]]
	+ [[#Linear Filters]]
	+ [[#Order-Statistic Filter]]
	+ [[#Iterative Truncated Arithmetic Mean Filter (ITM)]]
+ **Morphology**
	+ [[#Morphology and Set Theory]]
	+ [[#Dilation and Erosion]]
	+ [[#Opening and Closing]]

---
## Image Capture and Perception

+ **Image** - 2D projection of light from a 3D object or scene

Images are usually captured by a camera which is highly inspired by the human eyes. Since the camera is actually capturing light, the properties of light are deeply related to images.

+ **Color** - related to the light wavelength $\lambda$ on the spectrum
+ **Luminance** - related to the energy of light, a function of wavelength $I(\lambda)$

When a camera capture a image, the all-spectrum light luminance distribution is a function of 2D coordinate $x,y$
$$f(x,y)=\int_0^\infty I(x,y,\lambda)V(\lambda)\mathrm{d}\lambda$$
+ $I(\lambda)$ - the intensity of light reflected by the original object at the specific wavelength
+ $V(\lambda)$ - the wavelengths sensibility function of the camera perceptor 

Here's the color sensitivity of all 4 human eyes receptor cells

![[Pasted image 20250223082629.png]]

---
## Color Space

+ **Goal** - simplify the display of colors
+ **Make use of** - principle of human color vision

The light spectrum is continuous and contains countless of colors. It's technically not possible to display every color at its specific wavelength. However, owing to the fact that the human eyes only have 3 types of color rods. We can display all the colors use only **three** primary colors

Standard color spaces includes RGB, CMYB, YIQ, HSI, YCbCr

---
## Digitization and Resolution

+ **Goal** - reduce the information required to store an image

The digitization of a continuous image happens on both its space and intensity, the digitization precision is scaled by the **resolution**.

+ **Spatial** - the image is divided into $m\times n$ pixels and each stores a small region of spatial information
$$f(x,y)\to f(m,n)$$
+ **Intensity** - the real number intensity (grey level) is divided into finite levels, usually $2^b$ levels

The **Image Histogram** visualizes the grey level frequency distribution of pixels. Each bar of it represents the proportion of pixels at this grey level in the image. 
$$p_f(f)=\frac{n_f}{n}$$
+ $n_f$ - number of pixels with grey level $f$
+ $n$ - total number of pixels in the image

(See also [[#Histogram Equalization]])

---
## Linear Shift Invariant System (LSI)

Mathematically, digital image is a type of 2D discrete signal similar to time-based 1D signal. So any proporties or operations of signal apply to digial image as well.

+ **Impulse Image** $\delta(x,y)$ - the origin pixel $\delta(0,0)=1$, all other pixels have $\delta(x,y)=0$. Any digital image $f(x,y)$ can be represented as the sum of many **space-shifted** impulse image.
$$f(x,y)=\sum_{j=-\infty}^\infty\sum_{i=-\infty}^\infty f(i,j)\delta(x-i,y-j)$$

+ **Image Transform System** $T$ - the system receives an input image $f(x,y)$ and output a response image $g(x,y)$
$$g(x,y)=T\{f(x,y)\}$$
	+ **Impulse Response** $h(x,y)$ - the output response of the impulse Image as input
$$h(x,y)=T\{\delta(x,y)\}$$
	+ **Linearity** - if the transform can be placed into the linear combination
$$T\{af(x,y)+bg(x,y)\}=aT\{f(x,y)\}+bT\{g(x,y)\}$$
	+ **Shift Invariant** - if spatial-shifting the image doesn't change the output pattern
$$T\{f(x-i,y-j)\}=g(x-i,y-j)$$

---
## Convolution

The output image $g(x,y)$ of a LSI system $T$ is the convolution of its **impulse response image** $h(x,y)$ and the input $f(x,y)$
$$g(x,y)=h(x,y)*f(x,y)=\sum_{j=-\infty}^\infty\sum_{i=-\infty}^\infty f(i,j)h(x-i,y-j)$$
It means that **impulse response image** completely described the transform property of a LSI system. This yields the concept of **convolution kernel** in Image Processing

+ **Filter** - a LSI image processing system
+ **Spatial Representation** - the impulse response image of a filter
+ **Convolution Kernel** - the small version of the spatial representation

---
## Fourier Transform

The 2D discrete Fourier Transform maps a real spatial domain image $f(x,y)$ to the frequency domain complex image $F(u,v)$ which is the sum of components with different frequency

+ **Fourier Transform** ($m,n$ are row and column numbers)
$$F(u,v)=\sum_{x=0}^{m-1}\sum_{y=0}^{n-1}f(x,y)e^{-j2\pi(u\frac{x}{m}+v\frac{y}{n})}$$
+ **Inverse Transform**
$$f(x,y)=\frac{1}{mn}\sum_{u=0}^{m-1}\sum_{v=0}^{n-1}F(u,v)e^{-j2\pi(u\frac{x}{m}+v\frac{y}{n})}$$
After the transform, the low frequency components of the image are at the center

![[Pasted image 20250224171608.png]]

The 2D discrete Fourier Transform has similar properties as a continuous time Fourier Transform

+ **Linearity** - the transform of a linear combination of images can be put into the terms
$$\mathcal{F}\{af_1(x,y)+bf_2(x,y)\}=a\mathcal{F}\{f_1(x,y)\}+b\mathcal{F}\{f_2(x,y)\}$$
+ **Scaling** - stretching in the spatial domain leads to compression in the frequency domain, vice versa (don't forget the extra coefficient)
$$\mathcal{F}\{f(ax,by)\}=\frac{1}{|ab|}F(\frac{u}{a}, \frac{v}{b})$$
+ **Convolution Theorem** - convolution in the spatial domain is equvalent to the multiplication in the frequency domain, vice versa
$$f(x,y)*g(x,y)=F(u,v)G(u,v)$$
+ **Frequency Periodicity** - the complex image appears periodically in the frequency domain, this is owing to the periodicity of the complex exponential function
$$F(u+m,v+n)=F(u, v+n)=F(u+m,v)=F(u,v)$$
+ **Conjugate Symmetry**
$$F^*(-u,-v)=F(u,v)$$

---
## Image Sampling

The image sampling converts a spatial continuous image into a spatial discrete image. The spatial sampling period must be higher than 2 times **Nyquist frequency** of the orignal image to maintain all the information.

---
## Point Processing

Point processing algorithms process the image pixel-by-pixel regardless of their arrangement or adjacency.

+ **Simple Point Processing** - only consider the gray level of the input pixel
+ **Histogram Equalization** - rescale the pixel gray level based on the overall gray level distribution

The graph below shows common variants of Simple Point Processing

![[Pasted image 20250224133535.png]]

---
## Histogram Equalization 

+ **Goal** - increate the global contract
+ **Result** - cumulative distribution function (CDF) of histogram nearly uniform

Histogram Equalization is a special point processing algorithm that rescales the grey level bases on the global histogram, making the cumulative distribution function of the histogram to the approximation of a uniform distribution.

> [!NOTE] Histogram Equalization Equation $f\to g$
> $$g=\mathrm{round}(\frac{c(f)-c_\min}{1-c_\min}L)$$
> + $c(f)$ - cumulative distribution function of the histogram (CDF)
> + $c_{\min}$ - the grey level proportion of $f=0$ (smallest level of CDF)
> + $L$ - the largest grey level

+ **Histogram**
$$p_f(f)=\frac{n_f}{n}$$
+ $n_f$ - number of pixels with grey level $f$
+ $n$ - total number of pixels in the image

+ **Cumulative Distribution Function of the Histogram**
$$c(f)=\sum_{i=0}^f p_f(i)$$


![[Pasted image 20250224150144.png]]

---
## Linear Filters

+ **Goal** - make the image more sharp (high pass) or smooth (low pass)
+ **Pros & Cons** - easy to design but cause loss of certain frequency components

Linear Filters $H(u,v)$ are filters that works on the frequency domain of an image.

When mapped into the frequency domain using Fourier Transform, the image is decomposed into several frequency components.

+ **Low Frequency** components --> outlines (smooth)
+ **High Frequency** components --> details (sharp)

Smoothing and Sharpening of the image can be done by reducing one type of the components above

+ **Smoothing (Low Pass)** - push the image towards the average by reducing high frequency components
+ **Sharpening (High Pass)** - push the image towards details by reducing low frequency components

The filters can also be categoried by their shapes

+ **Ideal** - have discontinuities at the threshold that results in **Ringing Artifacts**
+ **Gaussian** - described by a 2D Gaussian function with good performance
	+ **Low Pass**
$$ G(u,v)=\frac{1}{2\pi\sigma^2}\exp({-\frac{u^2+v^2}{2D_o}})$$
	+ **High Pass**
$$ G(u,v)=1-\exp({-\frac{u^2+v^2}{2D_o}})$$
---
## Order-Statistic Filter

+ **Goal** - remove random noises
+ **Pros & Cons** - 

Orde-Statistic Filters are based on statistic result of pixel grey levels covered in the filter region. They're usually highly nonlinear.

+ **Mean** - smooth and blur the image, good for removing **additive Gaussian noise**
+ **Median** - good for removing **salt and pepper noise** 
+ Other Type - Max, Min
+ Advanced - ITM

---
## Iterative Truncated Arithmetic Mean Filter (ITM)

+ **Goal** - combine the merits of mean and median

ITM is a special Order-Statistic Filter invented by Prof. Jiang Xudong. It 





---
## Morphology and Set Theory

+ **Use on** - binary images
+ **Operations** - Dilation, Erosion, Opening, Closing

Morphology is a category of image processing algorithms for binary images. Its output is yielded from the logic operation of input images $A,B$ and thus greatly based on the set theory. 

+ Input $A$
+ Structural Element $B$





---
## Dilation and Erosion

Dilation and Erosion





---
## Opening and Closing



