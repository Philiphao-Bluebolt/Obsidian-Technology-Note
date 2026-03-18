[[#Exc 1 - Design a first order low-pass filter]]
[[#Exc 2 - Design a first order high-pass filter]]
[[#Exc 3 - Design a second order Sallen-Key low-pass filter]]
[[#Exc 4 - Design a second order band-pass filter]]
[[#Exc 5 - Buttonworth filter]]

---
## Exc 1 - Design a first order low-pass filter 

Design a first order RC active low-pass filter with $‒3\mathrm{dB}$ frequency of $10 \mathrm{kHz}$. Standard $10 \mathrm{k\Omega}$ resistor value is preferred.

The standard first-order low-pass filter is shown here so there's not much to do with the circuit structure. We just need to calculate the value of $R$ and $C$ in the circuit using frequency scaling and impedance scaling.
![[Pasted image 20241108163549.png]]
The frequency scaling coefficient $\alpha$ is computed by comparing the frequency response magnitude of the standard circuit and the desired circuit at the cutoff frequency
$$\alpha=\frac{\omega_c}{\lambda_c}=\frac{10\mathrm{kHz}}{1\mathrm{rad/s}}=2\times10^4\pi$$
Then we scale the capacitors. Divide them by $\alpha$
$$C=\frac{1F}{\alpha}=\frac{1}{2\times10^4\pi}\mathrm{F}$$
In order to use $10k\Omega$ resistors, impedance scaling is required. Scaling all the component values by the same coefficient doesn't affect the frequency response.
$$\beta=\frac{10k\Omega}{1}=10^{4}$$$$\beta X_C=\frac{1}{j\omega C/\beta}$$$$C=\frac{1\mathrm{F}}{2\times10^4\pi\times \beta}=1592\mathrm{pF}$$
The desired filter circuit
![[Pasted image 20241108164720.png]]

---
## Exc 2 - Design a first order high-pass filter

Design a first order RC active high-pass filter with $0 \mathrm{dB}$ gain at high frequencies and attenuation of $30 \mathrm{dB}$ at $40 \mathrm{Hz}$. Standard $4700 \mathrm{pF}$ capacitors are preferred for the design.

The first-order high-pass transfer function and structure is given here. This time, finding the frequency scaling coefficient become a little bit tricky. We must find the frequency with magnitude of $-30 \mathrm{dB}$ in standard function first.
$$H(s)=\frac{s}{s+1}$$
![[Pasted image 20241108164824.png]]
Firstly, find the frequency with magnitude of $-30 \mathrm{dB}$ in standard function
$$\begin{align}20\lg\frac{\lambda_0}{\sqrt{\lambda_0^2+1}}&=-30\\\lambda_0&=0.0316\quad\mathrm{rad/s}\end{align}$$
Then we can calculate the frequency scaling coefficient $\alpha$
$$\alpha=\frac{\omega_0}{\lambda_0}=\frac{40\mathrm{Hz}}{0.0316\mathrm{rad/s}}=7953.399$$
Calculate the capacitance
$$C=\frac{1\mathrm{F}}{\alpha}=125.7324\mathrm{\mu F}$$
Then do the impedance scaling on the resistors
$$R=1\mathrm{\Omega}\times\beta=1\mathrm{\Omega}\times\frac{125.7324\mu F}{4700\mathrm{pF}}=26.752\mathrm{k\Omega}$$
![[Pasted image 20241108172714.png]]


---
## Exc 3 - Design a second order Sallen-Key low-pass filter

Design a second order Sallen-Key low-pass filter with $Q =1.414$. It requires to provide an attenuation of $18.36 \mathrm{dB}$ at $60 \mathrm{kHz}$. Standard $2200 \mathrm{pF}$ capacitors are preferred in the design.

Although it switches to second order, the design method has no difference with first order filter.
$$H(s)=\frac{1}{s^2+\frac{1}{Q}s+1}$$
![[Pasted image 20241109115243.png]]
Find the $18.36 \mathrm{dB}$ attenuation frequency in the standard filter
$$\begin{align}20\lg|H(j\lambda)|=\frac{1}{\sqrt{(1-\omega^2)^2+(\frac{\omega}{Q})^2}}&=-18.36\mathrm{dB}\\\lambda&=3.00\mathrm{rad/s}\end{align}$$
The frequency scaling coefficient $\alpha$
$$\alpha=\frac{60\mathrm{kHz}}{3\mathrm{rad/s}}=1.2566\times10^5$$
Then calculate the capacitor values
$$C=\frac{1\mathrm{F}}{\alpha}=7.958\mathrm{\mu F}$$
Scale the resistors for using the $2200 \mathrm{pF}$ capacitors
$$R=1\Omega\times \beta=1\Omega \times\frac{7.958\mathrm{\mu F}}{2200\mathrm{pF}}=3.617\mathrm{k\Omega}$$
Remember, $A$ should be calculated as well
$$A=3-\frac{1}{Q}=2.293$$
Btw, the circuit multiply the pass band gain by $A$. If we need a unit pass band gain here, a multiplier must be added to reduce the gain.





---
## Exc 4 - Design a second order band-pass filter

Design a second order band-pass filter with $-3\mathrm{dB}$ bandwidth from $800 \mathrm{Hz}$ to $925 \mathrm{Hz}$ using the biquadratic filter. $1\mathrm{k\Omega}$ standard resistors are preferred for your design.

Biquadratic Filter has a band-pass output terminal whose transfer function is a standard band-pass filter with some extra gain. No need to worry about the gain difference as it doesn't affect the frequency characteristics.

$$H_{BP}(s)=-(2Q-1)\frac{\frac{1}{Q}s}{s^2+\frac{1}{Q}s+1}$$

![[Pasted image 20241109171238.png]]

First, we need to find the reference frequency $\omega_c$ of the desired function for frequency scaling. Notice that the band-pass graph is symmetrical about the reference frequency in frequency scale.
$$\begin{align}\lg\omega_c&=\frac{\lg\omega_L+\lg\omega_H}{2}\\\omega_c&=\sqrt{\omega_L\omega_H}\\\omega_c&=5405\quad\mathrm{rad/s}\end{align}$$
Now we have the frequency scaling coefficient
$$\alpha=\frac{\omega_c}{1\mathrm{rad/s}}=5405$$
The next stage is to calculate the parameter $Q$, it can be obtained by inspecting the pass-band length at the standard form before scaling. An attenuation of $-3\mathrm{dB}$ means the power decays by half.
$$\begin{align}|H(j\lambda)|^2=(\frac{\frac{\lambda}{Q}}{\sqrt{(1-\lambda^2)^2+(\frac{\lambda}{Q})^2}})^2&=\frac{1}{2}\\\lambda^2+\frac{1}{Q}\lambda-1&=0\end{align}$$
$$\begin{align}\lambda_H-\lambda_L=\frac{\sqrt{\Delta}}{a}=\sqrt{\frac{1}{Q^2}-4}&=\frac{\omega_H-\omega_L}{\alpha}\\Q&=0.2481\end{align}$$



---
## Exc 5 - Buttonworth filter

Design a maximally flat, low-pass, active filter with $-3\mathrm{dB}$ bandwidth of $3 \mathrm{kHz}$ and attenuation of at least $60 \mathrm{dB}$ at $15 \mathrm{kHz}$. $10\mathrm{k\Omega}$ resistors are preferred for your design.

Firstly, calculate the frequency scaling coefficient
$$\alpha=\frac{3\mathrm{kHz}}{1\mathrm{rad/s}}=6000\pi$$
The desired attenuation is compared to the standard bottonworth filter expression to calculate the required filter order.
$$\begin{align}20\lg\frac{1}{\sqrt{1+(\frac{15\mathrm{k}\times2\pi\mathrm{rad/s}}{6000\pi})^{2n}}}&<-60\mathrm{dB}\\10^6-1&<25^n\\n&>\log_{25}(10^6-1)\\n&>4.29\end{align}$$
So we choose the fifth order filter ($n=5$). Look up the Buttonworth table and write down the expression. Seem that the filter can be achieved by a first order filter and two second order filters.
$$H(s)=\frac{1}{(s+1)(s^2+0.6180s+1)(s^2+1.6180s+1)}$$
The rest work is to design three filters respectively and connect them together.


---
## Exc 6 - Chelychev filter

