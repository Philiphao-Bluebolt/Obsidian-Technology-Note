+ **Function** - Block some of the frequency factors of the signal while allowing others to pass

In a nutshell, filters are circuits that extinguish frequencies. They're created to get rid of unwanted signal component in certain frequency ranges. There're two types filters based on their components

+ Passive filter - Built with RCL impedance component
+ Active filter - Built with RC and active components, more **compact**.

> When designing a filter, we're actually finding a **transfer function** $H(s)$ with the desired frequency response and then build a circuit to implement the system. This method is called **Network Synthesis**

+ Design Technique
	+ [[#Frequency Scaling]]
	+ [[#Impedance Scaling]]
+ Filters
	+ [[#First Order Filter]]
		+ [[#First Order Low Pass]]
		+ [[#First Order High Pass]]
	+ [[#Sallen-key Second Order Filter]]
		+ [[#Second Order Low Pass Filter]]
		+ [[#Second Order High Pass Filter]]
		+ [[#Second Order Band Stop (Notch) Filter]]
	+ [[#Biquadratic Filter]]
	+ [[#Butterworth Filter]]
	+ [[#Chebyshev Filter]]

---
## Frequency Scaling

+ **Goal** - Design arbitrary filters based on the unit cutoff frequency "standard filters" 

There's a standard form for each filter typology whose resistors and capacitors have unit value. The transfer function of those standard forms are much simpler than the universal ones with resistor and capacitor values as parameters, thus suitable for design. 

Multiplying the frequency by $\alpha$ only swifts the characteristics graph horizontally and doesn't change the shape of the graph.

> Frequency Scaling - Scaling the frequency of the standard filters by $\alpha$ is equivalent to scaling the values of LC frequency sensative components. 

![[Pasted image 20241108173553.png]]

---
## Impedance Scaling

+ **Goal** - Adjust the values of RCL component to match the standard values

When building the filters with discrete components, only a few resistors and capacitors with standardized values are marketable. This is why we have to adjust the values of the components

> Impedance Scaling - If all the impedances of the components in the filter are **scaled by the same factor** $\beta$ , the frequency response of the filter remain **unchanged**. 
![[Pasted image 20241106123022.png]]

Assume the scaling factor is beta:

+ Resistor
$$R\quad\to\quad\beta R$$
+ Capacitor
$$X_C=\frac{1}{j\omega C} \quad\to\quad \beta X_C=\frac{1}{j\omega \frac{C}{\beta}}$$
+ Inductor
$$X_L=j\omega L \quad \to \quad \beta X_L=j\omega \beta L$$

> [!NOTE] Why is Impedance Scaling possible?
> This is because the filter's network transfer function **from input voltage to output voltage** (aka. trans-voltage) always has a base unit of 1, thus only relys on the ratio of impedances instead of the exact values.

---
## First Order Filter

First Order Filter is the simplest active filter category. However, they can only be low-pass filter or high-pass filter. No band-pass or band-stop characteristics is achievable by only using one energy-storing device.

### First Order Low Pass

+ Transfer Function
$$H(s)=\frac{1}{s+1}$$
+ Architecture
![[Pasted image 20241109125128.png]]

### First Order High Pass

+ Transfer Function
$$H(s)=\frac{s}{s+1}$$
+ Architecture
![[Pasted image 20241109125856.png]]

---
## Sallen-key Second Order Filter

Second Order Filter use two capacitors and has two poles. The Sallen-key topology is the most popular second order filter architecture. It is one of the VCVS architecture

### Second Order Low Pass Filter

+ Transfer Function
$$H(s)=\frac{1}{s^2+\frac{1}{Q}s+1}$$
+ Architecture
![[Pasted image 20241109155603.png]]


### Second Order High Pass Filter

+ Transfer Function
$$H(s)=\frac{s^2}{s^2+\frac{1}{Q}s+1}$$
+ Architecture
![[Pasted image 20241109155614.png]]

### Second Order Band Stop (Notch) Filter

+ Transfer Function
$$H(s)=\frac{s^2+1}{s^2+\frac{1}{Q}s+1}=H_{HP}+H_{LP}$$
+ Architecture - Adding the output of high-pass and low-pass filter


---
## Biquadratic Filter

Biquadratic Filter is a special circuit that implements second order low-pass, high-pass and band-pass filters simultaneously. It's based on the fact that the three types of second order filter are related by an intergral $\frac{1}{s}$.
$$H_{HP}(s)=\frac{s^2}{s^2+\frac{1}{Q}s+1} \longrightarrow H_{BP}(s)=\frac{\frac{1}{Q}s}{s^2+\frac{1}{Q}s+1}\longrightarrow H_{LP}(s)=\frac{1}{s^2+\frac{1}{Q}s+1}$$
A typical biquadratic filter is derived from the second order low pass transfer function.
$$\begin{align}\frac{v_{LP}}{v_i}&=\frac{1}{s^2+\frac{1}{Q}s+1}\\v_i&=s^2v_{LP}+\frac{1}{Q}sv_{LP}+v_{LP}\\v_i&=v_{HP}+v_{BP}+v_{LP}\\v_{HP}&=v_i-v_{BP}-v_{LP}\\\end{align}$$
Then the function could be described by the high pass output $v_{HP}$ 
$$v_{HP}=v_i-\frac{1}{sQ}v_{HP}-\frac{1}{s^2}v_{HP}$$
This can be achieved by an adder-subtractor and two serial integrators. Notice the control of parameter $Q$ is not inplemented at the intergrator, but at the feedback subtracting resistor $R_{2Q-1}$


![[Pasted image 20241110144700.png]]

Similar to Sallen-key filter, the side effect of redendancy gain is existed in biquadratic filter. It can be eliminated by a multiplier.

---
## Butterworth Filter

Buttonworth Filter is a family of the low pass filters whose magnitude frequency response is described as
$$|H(j\omega)|=\frac{1}{\sqrt{1+\omega^{2n}}}$$
Buttonworth Filter can be built by connecting several first order and second order based on the Bottonworth table.

---
## Chebyshev Filter

