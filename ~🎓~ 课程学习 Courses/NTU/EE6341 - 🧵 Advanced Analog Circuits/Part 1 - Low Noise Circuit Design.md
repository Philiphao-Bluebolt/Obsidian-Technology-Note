
+ [[#Noise in the circuit]]
+ [[#How to describe a Noise]]
+ [[#Equivalent Noise Bandwidth]]
+ [[#Types of Noise]]


---
## Noise in the circuit

+ **Cause** - Unavoidable fluctuations of voltage and current in components
+ **Characteristics** - Random, Unpredictable, Indeterministic
+ Noise Floor - Sensitivity of a system

High Noise Floor results in inability to distinguish signal and noise

---
## How to describe a Noise

> Random process against a random signal.

+ Probability Density Function (PDF) - Time Domain Characteristics 
+ Power Spectral Density (PSD) - Frequency Domain Characteristics

In a electrical circuit, a noise emerges in the form of voltage or current, but we're more interested in the power it produces rather than its own value.
$$P=UI=\frac{U^2}{R}=I^2R$$
The square of the value of a noise $x(t)$ is equal to the power in quantity.

+ Noise Power (MS Intensity) - The average **power** of a noise $x(t)$ over a long period of time
$$\bar{X^2}=\lim_{T\to\infty}\frac{1}{T} \int_0^T x^2(t)dt$$
+ RMS - The root of Noise Power, a common representation for electric signal (Unit: $V$ or $A$)
$$X_{rms}=\sqrt{\bar{X^2}}$$
+ Power Spectral Density - A function of frequency (Unit: $V^2/Hz$ or $A^2/Hz$)
$$\bar{x^2}(t)=\frac{\bar{X^2}}{\Delta f}$$
$\Delta f$ is the equivalent noise bandwidth of the system

---
## Equivalent Noise Bandwidth



---
## Types of Noise

Noises in a circuit result from different physical property.

| Noise Type                              | Related Component             | Cause                                | Condition of Present                  | PSD                                      |
| --------------------------------------- | ----------------------------- | ------------------------------------ | ------------------------------------- | ---------------------------------------- |
| Thermal noise (Johnson–Nyquist noise)   | Resistor                      | Electron thermal agitation           | No (always present)                   | $$\bar{v^2}=4kTR$$                       |
| Shot noise                              | PN Junction (Diode, BJT, MOS) | Electron crosses a potential barrier | DC biasing current exists             | $$\bar{i^2}=2qI$$                        |
| Burst noise (Popcorn noise)             | Dicrete Transistors           | Heavy-metal ion<br>contamination     | DC biasing current exists             | $$\bar{i^2}=k_2\frac{I^c}{1+(f/f_c)^2}$$ |
| Flicker noise ($1/f$ noise)             | All devices                   | Imperfections in manufacturing       | DC biasing current exists             | $$\bar{i^2}=k_1\frac{I^a}{f}$$           |
| Excess Noise (One of the Flicker noise) | Resistor                      | Imperfections in manufacturing       | DC voltage across the resistor exists | $$\bar{v^2}=\frac{m^2 V^2}{f}$$          |


---
## Noise Source Combination

