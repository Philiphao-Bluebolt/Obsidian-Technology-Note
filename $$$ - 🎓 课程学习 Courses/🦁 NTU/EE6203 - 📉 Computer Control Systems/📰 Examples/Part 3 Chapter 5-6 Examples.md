
+ [[#Digital Controller Design]]
	+ [[#5-1 Obtain the digital controller using Pole-Zero Matching]]
	+ [[#5-2 Obtain the digital controller using Pole-Zero Matching 2]]
	+ [[#5-3 Design a cruise control system for a car]]
	+ [[#5-4 Extra zeros by w-bilinear transform]]
	+ [[#5-5 Frequency domain digital controller design]]
	+ [[#5-6 Direct closed-loop design]]
	+ [[#5-7 Direct closed-loop design with unstable poles or zeros]]
	+ [[#5-9 & 10 Deadbeat controller design (intersample oscillation)]]
	+ [[#5-11 Ripple-free deadbeat controller design]]
	+ [[#5-12 Ripple-free deadbeat controller design 2]]
	+ 
+ [[#Digital Controller Implementation]]
	+ [[]]

---
## Digital Controller Design

#### 5-1  Obtain the digital controller using Pole-Zero Matching

Find a pole-zero matched digital filter approximation for the analog filter for a sampling period $T=0.1\mathrm{s}$. The damping ratio is $0.5$ and the undamped natural frequency is $5\mathrm{rad/s}$
$$G_a(s)=\frac{\omega_n^2}{s^2+2\xi\omega_ns+\omega_n^2}$$
The controller has two poles and no zero
$$p_{1,2}=-\xi\omega_n\pm \omega_n\sqrt{\xi^2-1}=-\xi\omega_n\pm j\omega_d$$
So the digital controller would be
$$\begin{align}G(z)&=\frac{(z+1)\alpha}{(z-e^{(-\xi\omega_n+ \omega_d)T})(z-e^{(-\xi\omega_n- \omega_d)T})}\\&=\frac{(z+1)\alpha}{z^2-z(e^{(-\xi\omega_n+ \omega_d)T}+e^{(-\xi\omega_n- \omega_d)T})+e^{-2\xi\omega_n T}}\\&=\frac{(z+1)\alpha}{z^2-ze^{-\xi \omega_nT}\cos(\omega_dT)+e^{-2\xi\omega_n T}}\\&=\frac{(z+1)\alpha}{z^2-1.414z+0.6065}\end{align}$$

The last step is to adjust the discrete gain $\alpha$
$$\begin{align}G(z=1)&=G_a(s=0)\\\frac{2\alpha}{1-1.414+0.6065}&=1\\\alpha&=0.09625\end{align}$$
So we have
$$G(z)=\frac{0.09625(z+1)}{z^2-1.414z+0.6065}$$

#### 5-2  Obtain the digital controller using Pole-Zero Matching 2

Derive the digital controller with sampling period $T=0.02\mathrm{s}$. The damping ratio is $0.88$ and the undamped natural frequency is $1.15\mathrm{rad/s}$
$$G_a(s)=\frac{1.322}{s^2+2.024s+1.322}$$
Step 1 - Map all the zeros and poles to z domain.
$$G(z)=\frac{1}{(z^2-2ze^{-\xi\omega_nT}\cos(\omega_d T)+e^{-2\xi\omega_n T})}=\frac{1}{z^2-1.96z+0.96}$$
Step 2 - Add a extra zero
$$G(z)=\frac{z+1}{z^2-1.96z+0.9603}$$
Step 3 - Adjust gain
$$G(z=1)=G_a(s=0)$$$$G(z)=1.5\times10^{-4}\frac{z+1}{z^2-1.96z+0.9603}$$
#### 5-3  Design a cruise control system for a car

A car has a weight $m=1000\mathrm{kg}$ and the average friction coefficient $b=100$. Design a cruise control system for the car so that the speed can reach $100\mathrm{km/h}$ from $0\mathrm{km/h}$ in $8\mathrm{s}$ with a overshoot less than $20\%$




#### 5-4  Extra zeros by w-bilinear transform

Consider the cruise control system with the following transfer function. Transfer it to a discrete system and do frequency analysis based on the w-bilinear transform. Compare the result of difference sampling period $T=0.1\mathrm{s}$ and $T=0.01\mathrm{s}$
$$G(s)=\frac{1}{s+1}$$
Use zero-pole matching and w-bilinear transform $z=\frac{1+\frac{wT}{2}}{1-\frac{wT}{2}}$
$$T=0.1\mathrm{s}\quad \quad G(z)=\frac{0.0952}{z-0.9048}\quad \quad G(w)=\frac{}{}$$
$$T=0.01\mathrm{s}\quad \quad G(z)=\frac{0.00995}{z-0.99}\quad \quad$$

#### 5-5  Frequency domain digital controller design




#### 5-6  Direct closed-loop design

Design a digital controller with its output to a zero-order-hold for the DC motor speed control
system with the following analog transfer function. The unit step response of the system should be zero steady-state error and have a settling time of $4\mathrm{s}$ (Tolerance of $5\%$). Sampling period $T=0.02\mathrm{s}$
$$G(s)=\frac{1}{(s+1)(s+10)}$$
Firstly, calculate the discrete controlled $G_{ZAS}(z)$ using Z transform which composed of the zero-order-hold and the DC motor.
$$\begin{align}G_{ZAS}(z)=Z\{\frac{1-e^{-Ts}}{s}G(s)\}&=(1-z^{-1})Z\{\frac{G(s)}{s}\}\\&=(1-z^{-1})Z\{\frac{1}{10s}-\frac{1}{9(s+1)}+\frac{1}{90(s+10)}\}\\&=(1-z^{-1})(\frac{1}{10(1-z^{-1})}-\frac{1}{9(1-e^{-T}z^{-1})}+\frac{1}{90(1-e^{-10T}z^{-1})})\\&=1.8604\times 10^{-4}\frac{z+0.9293}{(z-0.8187)(z-0.9802)}\end{align}$$
The next step is to choose a continuous closed-loop function satisfying the conditions. 

+ The degree of the discretized system is 2, so the closed-loop function should have at least 2 degree. A second order system with no zero is preferable.
+ The settling time $T_s$ can be described by the damping ratio $\xi$ and undamped natural frequency $\omega_n$
$$T_s(5\%)=\frac{4}{\xi \omega_n}=4\mathrm{s}$$
So we can choose $\xi=0.88$ and $\omega_n=1.15\mathrm{rad/s}$ and write down the continuous time transfer function
$$$$


#### 5-7  Direct closed-loop design with unstable poles or zeros

Design a digital controller for the type 0 analog plant. The unit step response of the system should be zero steady-state error and have a settling time of $10\mathrm{s}$ ($5\%$ Tolerance) with no overshoot. Sampling period $T=1\mathrm{s}$
$$G(s)=\frac{1}{10s+1}e^{-5s}$$


#### 5-8  Deadbeat controller design

Design a controller for the following discrete zero-hold analog system and achieve deadbeat control.
$$G_{ZAS}(z)=\frac{z^{-2}}{1-z^{-1}}$$
Change the form of the system to
$$G_{ZAS}(z)=\frac{z^{-2}}{1-z^{-1}}=\frac{1}{z(z-1)}$$
The system has two poles and no zeros, thus has a degree of 2, the closed-loop transfer function should be at least $z^{-2}$. Notice that there is a critical unstable pole in $G_{ZAS}(z)$ and it's eliminated by $1-G_{cl}(z)$
$$\begin{align}C(z)&=\frac{1}{G_{ZAS}(z)}\frac{G_{cl}(z)}{1-G_{cl}(z)}\\&=z(z-1)\frac{z^{-2}}{1-z^{-2}}\\&=\frac{z}{z+1}\end{align}$$
So the deadbeat controller is
$$C(z)=\frac{z}{z+1}$$

#### 5-9 & 10  Deadbeat controller design (intersample oscillation)

Design a deadbeat controller with its output to a zero-order-hold for the DC motor speed control system with an analog transfer function.
$$G(s)=\frac{1}{(s+1)(s+10)}$$

#### 5-11  Ripple-free deadbeat controller design 

Design a ripple‐free deadbeat controller with ZOH for the type 1 vehicle positioning system whose
transfer function is the following (sampling period $T=0.1\mathrm{s}$)
$$G(s)=\frac{1}{s(s+1)}$$
Discretize the controlled system into $G_{ZAS}$
$$\begin{align}G_{ZAS}(z)=Z\{\frac{1-e^{-Ts}}{s}G(s)\}&=(1-z^{-1})Z\{\frac{G(s)}{s}\}\\&=(1-z^{-1})Z\{ \frac{1}{s+1}+\frac{1}{s^2}-\frac{1}{s} \}\\&=(1-z^{-1})(\frac{1}{1-e^{-T}z^{-1}}+\frac{Tz^{-1}}{(1-z^{-1})^2}+\frac{1}{1-z^{-1}})\\&=\frac{2z^2-3.805z+1.814}{(z-0.905)(z-1)}\end{align}$$
The control signal $U(z)$ is described as the following equation. Input reference unit step $R(z)=\frac{1}{1-z^{-1}}$ and the discretized system is known.
$$U(z)=\frac{Y(z)}{G_{ZAS}(z)}=\frac{Y(z)}{R(z)}\frac{R(z)}{G_{ZAS}(z)}=G_{cl}(z)\frac{R(z)}{G_{ZAS}(z)}=G_{cl}(z)\frac{}{}$$

#### 5-12  Ripple-free deadbeat controller design 2

Design a ripple‐free deadbeat controller with ZOH for the DC motor speed control system whose transfer function is
$$G(s)=\frac{1}{(s+1)(s+10)}$$

#### 5-13



---
## Digital Controller Implementation

#### 6-1  Representing