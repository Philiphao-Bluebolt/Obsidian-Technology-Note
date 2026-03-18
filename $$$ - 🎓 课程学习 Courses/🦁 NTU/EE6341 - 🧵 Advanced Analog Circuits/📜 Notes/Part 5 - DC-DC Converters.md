+ **Function** - Change the DC voltage and conserve the power

DC-to-DC Converters are intended to work as a DC voltage "transformer" with little or no power loss since AC transformer doesn't work on DC voltages. Thus, they're usually built with lossless component such as switch, capacitor and inductor to maintain a high power efficiency.

+ [[#Prototype]]
	+ [[#Linear Voltage Regulator]]
	+ [[#Switching Converter]]
+ [[#Switching-mode Configurations]]
	+ [[#Common Analysis Method]]
	+ [[#Buck]]
	+ [[#Boost]]
	+ [[#Buck-Boost]]
	+ [[#Cuk]]
+ [[#Non-ideal Effects]]


---
## Prototype

Here are two conceptual designs of DC-DC converter, they're not applicable but derives the requirements for a good DC-DC converter.

### Linear Voltage Regulator

+ **Advantage** - Changable reference voltage
+ **Drawback** - Efficiency dependent to output voltage

Linear Voltage uses a transistor as switch and a feedback Op Amp to set the reference output voltage. When the reference voltage is positive, the transistor will be active and create a negative feedback path for the Op Amp, thus the output voltage is set to be equal to the reference.

The major drawback of this configuration is that the power efficiency is determined by the output voltage. Since the input source and the output load shares the same current ($I_E\approx I_C$), a lower output voltage leads to lower power absorbed by the load. The ramain power is dissipated at the transistor, which is a great waste.
$$\begin{align}P_S&=P_T+P_L\\V_SI&=V_{CE}I+V_LI\end{align}$$
![[Pasted image 20241201145609.png]]


### Switching Converter

+ **Advantage** - No energy loss
+ **Drawback** - Rippling output voltage

Since transistors are unavoidably energy lossy as switch, replacing them with actual switches may fix. This yields the switching converter.

The switch is controlled by a high-frequency clock signal, making the output voltage a PWM wave whose average is the desired voltage. However, the fluctuating output voltage makes it nonapplicable.

![[Pasted image 20241201150201.png]]

---
## Switching-mode Configurations

Switching-mode DC-DC converters are the most efficient configurations. Ideally their efficiency can reach $100\%$ if the lossy imperfect parasite resistances are neglected. In reality, their efficiency is above $90\%$

All switching-mode converters share the following characteristics.

+ **Energy Conversion Component** - Usually inductors and capacitors
+ **Smoothing Capacitor** - parallel to the output load

### Common Analysis Method



| Type       | Input-output            | Inductor                         | Capacitor                                     |
| :--------- | :---------------------- | :------------------------------- | :-------------------------------------------- |
| Buck       | $V_o=DV_S$              | $L_{\min}=\frac{(1-D)R}{2f}$     | $C=\frac{(1-D)}{8Lf^2\frac{\Delta V_o}{V_o}}$ |
| Boost      | $V_o=\frac{V_S}{1-D}$   | $L_{\min}=\frac{D(1-D)^2R}{2f}$  | $C=\frac{D}{Rf\frac{\Delta V_o}{V_o}}$        |
| Buck-Boost | $V_o=-\frac{DV_S}{1-D}$ | $L_{\min}=\frac{(1-D)^2R}{2f}$   | $C=\frac{D}{Rf\frac{\Delta V_o}{V_o}}$        |
| Cuk        | $V_o=-\frac{DV_S}{1-D}$ | $L_{1\min}=\frac{(1-D)^2R}{2Df}$ |                                               |




### Buck 



### Boost



### Buck-Boost



### Cuk


---
## Non-ideal Effects

