+ [[#Tutorial 6 - Power Amplifier Class A]]
	+ [[#Questions]]
	+ [[#Solutions]]
	+ [[#6-1 Class A common-emitter conversion efficiency]]
	+ [[#6-2 Class A emitter follower conversion efficiency]]
	+ [[#6-3 Class A BiCMOS emitter follower]]

---
## Questions

![[EE4341-EE6341 Tutorial 6.pdf]]

---
## Solutions

![[63545042.pdf]]


---
## 6-1  Class A common-emitter conversion efficiency

### (a) 

To find the highest efficiency, we need to write down the equation of efficiency w.r.t the $R_C$ resistor. Before that, we should know the maximum possible output voltage swing.

![[Pasted image 20241110154418.png]]

When the circuit has no AC input, it only presents DC response current and voltage. Which is known as the Q point. Usually, the Q point is biased at the center of DC load line for maximum output swing.

+ DC output loop equation
$$V_{CC}=R_CI_{CQ}+V_{CEQ}$$
When there is AC input, the input signal will generate currents and voltages at the output loop, result in fluctuation. According to superpostion, the resulting voltages and currents are the sum of both DC and AC response. We denote the AC response collector current as $i_c'$ here.
$$\begin{cases}i_c=I_C-i_c'\\v_{ce}=V_{CEQ}+i_c'(R_L//R_C)\end{cases}$$
+ AC output loop equation
$$v_{ce}=V_{CEQ}+I_C(R_L//R_C)-i_c(R_L//R_C)$$
Actually, there are two extra conditions that guarantee the transistor to be at the active region. The collector current should always flows into the transistor and never changes direction and the collector-emitter voltage drop should be always greater than the saturation voltage drop. Therefore, the AC current $i_c'$ will never exceed $I_C$
$$\begin{cases}i_c>0\\v_{ce}>v_{ce,sat}=0V\end{cases}$$
Now we can draw both the DC and AC load line.  
![[Pasted image 20241110170220.png]]
The maximum peak voltage of the load can see from the graph
$$V_p=I_{CQ}(R_L//R_C)$$
Next stage is the calculate the efficiency. When calculating source power supply, the base bias $I_B$ current is often neglected for being too small.
$$\eta=\frac{P_L}{P_S}=\frac{\frac{V_p}{\sqrt{2}}\frac{I_p}{\sqrt{2}}}{V_{CC}I_{CQ}}=\frac{V_p^2}{2R_L}\frac{1}{V_{CC}\frac{V_{CC}}{2R_C}}=\frac{R_CR_L}{4(R_C+R_L)^2}$$
Use derivative to find out $R_C$ for a maximum efficiency
$$R_C=R_L=100\Omega$$
### (b) 

Since $R_C$ is known now, it;'s pretty simple to get all the bias values
$$I_{CQ}=\frac{V_{CC}-V_{CEQ}}{R_C}=60\mathrm{mA}$$
$$R_B=\frac{V_{CC}-V_{BEQ}}{I_B}=\frac{V_{CC}-V_{BEQ}}{\frac{I_C}{\beta}}=56.5\mathrm{k\Omega}$$
### (c) 

We always know how to calculate the maximum peak voltage of the load
$$V_p=I_{CQ}(R_L//R_C)=3\mathrm{V}$$
$$I_p=\frac{V_p}{R_L}=30\mathrm{mA}$$
The maximum efficiency (Shall it include $I_B$?)
$$\eta_{\mathrm{max}}=\frac{R_CR_L}{4(R_C+R_L)^2}=6.25\%$$

---
## 6-2  Class A emitter follower conversion efficiency

### (a)

Firstly, the relationship between $R$ and $I_Q$ is quiet straight-forward
$$I_Q=\frac{V_{CC}-V_{BE}}{R}$$
![[Pasted image 20241110201103.png]]
When the output voltage becomes negative, the maximum negative swing is determined by two conditions. Usually, the first condition is the privileged limit.

+ Whether the amplifier transistor $Q_1$ is cut-off, at which $i_{E1}=0$
$$I_Q+i_L=i_{E1}=0$$
+ Whether the mirror transistor $Q_2$ is saturated
$$i_L R_L=-V_{CC}+V_{CE,sat}$$

However, if we keep increasing the current mirror supply $I_Q$, then $Q_1$ will not be easily cut-off. If $I_Q$ is high enough, $Q_1$ will never cut-off and the output negative maximum swing will be limited by the saturation of $Q_2$ instead.
$$\frac{-V_{CC}+V_{CE,sat}}{R_L}=-I_Q$$
We can solve that
$$I_Q=9.8\mathrm{mA}$$
$$R=948.98\Omega$$
### (b) 

We already set $I_Q=9.8\mathrm{mA}$

+ Output current $i_L$ reaches maximum peak along with output voltage when $Q_1$ is saturated. Emitter current $i_{E1}$ reaches maximum at this time as well.
$$i_{L-max}=\frac{V_{CC}-V_{CE,sat}}{R_L}=9.8\mathrm{mA}$$
$$i_{E1-max}=i_{L-max}+I_Q=19.6\mathrm{mA}$$
+ $i_L$ reaches minimum (negative) peak when $Q_2$ is saturated. Emitter current $i_{E1}$ is depleted to zero at this time.
$$i_{L-min}=\frac{-V_{CC}+V_{CE,sat}}{R_L}=-9.8\mathrm{mA}$$
$$i_{E1-min}=i_{L-min}+I_Q=0$$

### (c)

The average power of AC output is quiet obvious
$$P_L=\frac{V_p}{\sqrt{2}}\frac{I_p}{\sqrt{2}}=\frac{1}{2}I_p^2R_L=0.048\mathrm{W}$$
The calculation of DC power is quiet tricky though. When AC input $v_i=0$, the load current is small as neglectable. This means that the DC current flowing through $Q_1$ and $Q_2$ is $I_Q$ and we have another $I_Q$ flowing through $Q_3$ as well. So here comes
$$P_S=I_Q[0-(-V_{CC})]+I_Q[V_{CC}-(-V_{CC})]=0.294\mathrm{W}$$
So the conversion efficiency
$$\eta=\frac{P_L}{P_S}=16.33\%$$

---
## 6-3  Class A BiCMOS emitter follower

