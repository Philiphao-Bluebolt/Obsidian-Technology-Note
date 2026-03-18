+ **Goal** - Derive the model of digital control system from mathematical theory

+ [[#Signal Sampler and Holder (ADC & DAC)]]
	+ [[#Ideal Impulse Sampler]]
	+ [[#Zero-order Holder (ZOH)]]
	+ [[#First-order Holder (FOH)]]
+ [[#Pulse Transfer Function]]


---
## Signal Sampler and Holder (ADC & DAC)

+ **Goal** - Convert between continuous-time signal and discrete-time signal

Digital controller accepts discrete reference and feedback signals and output discretes control signals, thus ADC and DAC are required to connect the controller to continuous plants.

### Ideal Impulse Sampler




### Zero-order Holder (ZOH)

Zero-order holder is the most common holder model and is used in almost every DAC.
$$G(s)=\frac{1-e^{-Ts}}{s}$$
The Z transform of ZOH together with the plant $G_{plant}(s)$
$$G_{ZAS}=Z\{G_{ZOH}(s)G_{plant}(s)\}=(1-z^{-1})Z\{\frac{G_{plant}(s)}{s}\}$$

### First-order Holder (FOH)

First-order holders are types of conceptual holders that use linear segments to rebuild the continuous signal. They're not widely used in industry and only discussed for academic purposes.

+ Predictive First-order Holder
$$G(s)=(\frac{1-e^{-Ts}}{s})^2 \frac{Ts+1}{T}$$
---
## Pulse Transfer Function


