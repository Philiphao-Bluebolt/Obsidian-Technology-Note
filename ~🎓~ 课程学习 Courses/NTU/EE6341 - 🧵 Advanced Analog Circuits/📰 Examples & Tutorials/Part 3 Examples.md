
+ Amplifier Basis 
	+ [[#Exc 1 - Q-point for a maximum swing]]
+ Class A
+ Class B
+ Class AB
+ Class C
+ Class D
+ Heat Sink


---
## Exc 1 - Q-point for a maximum swing

Determine the value of R1 and R2 providing maximum output voltage swing for the following amplifier and calculate the conversion coefficient when $v_{i_{peak}}=0.2V$

(Assuming $\beta=25, V_T=26mV, V_{BE}=0.7V, V_{CEsat}=0.2V,R_1=R_2$)
![[Pasted image 20241016104050.png]]

### (a) Calculate R1 and R2 

While analyzing the DC equipvalent circuit, open-circuit all the capacitors.

The Q-point we're finding is the DC voltage $V_{CE}$. To obtain the maximum output voltage swing, $V_{CE}$ should be the half of $V_{CC}$
$$V_{CEQ}=\frac{1}{2}V_{CC}=10V$$
Collector current $I_{CQ}$ can be obtained by solving the voltage equation of the collector-emitter pathway
$$\begin{align}V_{CEQ}&=V_{CC}-I_{CQ}R_C-I_{EQ}R_E\\I_{CQ}&=\frac{V_{CC}-V_{CEQ}}{R_C+\frac{1+\beta}{\beta}R_E}=90.58mV\end{align}$$
Base current $I_B$ and collector current $I_C$ are related by $\beta$
$$I_{BQ}=\frac{I_{CQ}}{\beta}=3.62mV$$
In order to simplify the calculate of $R_1$ and $R_2$, we apply Thevenin's equivalent method to the input side. Believe me, this stage is a bit tricky. 

![[Pasted image 20241017174726.png]]

Then the value of $R_1//R_2$ can be solved by applying KVL to the input pathway (As $R_1=R_2$)
$$V_{TH}=(R_1//R_2)I_{BQ}+V_{BE}+R_EI_{EQ}=10V$$
Finally we have
$$\begin{align}R_1//R_2&=2.31k\Omega\\R_1=R_2&=4.62k\Omega\end{align}$$
### (b) Calculate AC maximum swing

The AC equipvalent circuit (Here we use the simply Hybrid-pi model of BJT)
$$R_1//R_2=2.31k\Omega$$
$$R_C//R_L=7.41\Omega$$
![[Pasted image 20241017181013.png]]

Theoretically, the output voltage should be $5.16V$ since the peak of input signal is $0.2V$
$$v_o=g_mv_i(R_C//R_L)=\frac{I_C}{V_T}(R_C//R_L)v_i=5.16V$$
However, if $v_o=5.16V$, then the load current could be
$$i_L=\frac{R_L}{v_o}=645mA$$



---
## Exc 2 - 