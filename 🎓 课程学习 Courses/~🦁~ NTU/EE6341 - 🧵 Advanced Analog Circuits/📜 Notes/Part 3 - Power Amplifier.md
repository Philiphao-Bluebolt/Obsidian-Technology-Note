+ **Function** - Amplify the input signal and increase the power receives by the load

+ [[#Performance Metrics]]
	+ [[#Conversion Efficiency]]
	+ [[#Total Harmonic Distortion]]
+ [[#Typical BJT Amplifier]]
+ [[#Classes of Power Amplifiers]]
	+ [[#Class A]]
	+ [[#Class B]]
		+ [[#Crossover Distortion]]
+ [[#Heat Sink]]

---
## Performance Metrics

### Conversion Efficiency

+ **Goal** - Measure the efficiency of the power amplifier

Conversion Efficiency shows what percentage of DC source energy is received by the load i.e. the output signal power to the DC source power. The remain energy is lost as heat.
$$\eta=\frac{\bar{P}_L}{\bar{P}_S}$$
+ $P_L$ - DC source power
+ $P_S$ - Power receives by the load

Actually, the input signal has power as well, but it's too little compared to the DC power thus neglected. The complete energy equation is like
$$P_i+P_S=P_L+P_T$$
+ $P_i$ - Input signal power (very small)
+ $P_T$ - Thermal energy

### Total Harmonic Distortion (THD)

+ **Goal** - Measure the output distortion of the power amplifier

Total Harmonic Distortion measures how pure a sine signal is. It is defined as the RMS ratio of harmonic factors higher than second harmonic and the fundamental (first harmonic) 

$$THD=\frac{\sqrt{V^2_2+V^2_3+...}}{V_1}$$

+ $V_1$ - RMS of the fundamental frequency factor
+ $V_2, V_3, ...$ - RMS of the higher harmonic factors

---
## Typical BJT Amplifier

The maximum output voltage swing of a common-emitter BJT amplifier is determined by the DC power voltage $V_{CC}$ and the Q point. The allowed maximum swing here could be distortive.

![[Pasted image 20241016103446.png]]


---
## Classes of Power Amplifiers

Power Amplifiers are classified into a few classes based on the **Q point position** or **Active Angle** of each BJT in the circuit.

Class D is special as a digital power amplifier based on PWM. 

Nowaday, Class AB and Class D are most widely used.


---
## Class A 

+ **Linearity** - Good
+ **Efficiency** - Low 




---
## Class B

+ **Linearity** - Bad (Crossover Distortion)
+ **Efficiency** - High



### Crossover Distortion

Crossover Distortion happens when the state of two BJTs switchs. It's mainly owing to the existence base-emitter threshold voltage.





---
## Class C

+ **Linearity** - Bad
+ **Efficiency** - High

---
## Class AB

+ **Linearity** - Good
+ **Efficiency** - High



---
## Class D

+ **Linearity** - Good
+ **Efficiency** - High


---
## Heat Sink

Heat sink is a metal frame attached to a power transistor intended to prevent overheat. Whether a transistor need a heat sink or not depends on its energy dissipation process and the maximum heat it can tolerate.

The thermal resistance and 