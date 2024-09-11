
+ [[#Low Noise Circuit Design]]
	+ [[#Introduction to Circuit Noise]]
	+ [[#Noise model of semiconductor components]]
	+ [[#Noise Analysis]]
	+ [[#Tutorial 1-4]]
+ [[#Wideband Amplifier Design]]
[[#💡 Random Thoughts]]

---
## Low Noise Circuit Design

### Introduction to Circuit Noise

> [!FAQ] In the noise PSD definition formula $\overline{x^2}(f)=\overline{X^2}/\Delta f$, $\overline{X^2}$ is a variable and $\Delta f$ is a constant. How can their division become a function?
> Actually, the dependent chain works like this: The PSD $\overline{x^2}(f)$ is decided by the circuit parameters, such as resistor value $R$, temperature $T$ or bias current $I$, depending on their noise type. So, the PSD could be a function of frequency or a constant depending on the expression of the noise type. If the PSD is a function, then the MS $\overline{X^2}$ will be a function.

> [!FAQ] When two uncorrelated noise combine, why does $\overline{v_1 v_2}=0$ ?
>

> [!FAQ] As Burst, Flicker and Shot Noise are not related to resistance, they can not be transformed into a voltage form using the Thevenin's theorem or Norton's theorem and only have current form. Is that right?
>



> [!FAQ] Since the direction of the noise sourse is not that important. If the final result of noise response expression contains a minus symbol (for example, $\overline{u_o^2}=-C\overline{u^2}$) , can I just remove it?
> Yes, the direction of noise source is random so you don't need to care about the actual direction although you might need to anticipate a psudo-direction for calculation. In fact, since the response of the noise source is represented with PSD $\overline{u_o^2}$ as well, so any minus symbol will be cancelled out by the square.


> [!FAQ] The frequency output response of a input noise PSD through a network $H(j\omega)$ is depicted as $\overline{v_o^2}=|H(j\omega)|^2\overline{v_i^2}$. Why does the absolute of network function in the equation have square? Why don't the calculation of noise PSD need integration?
> In a nutshell, that square comes from the power.



> [!FAQ] Can you use equivalent noise bandwidth to calculate the RMS voltage of those noises that is a function of frequency $f$
> 

> [!FAQ] Why can't we directly sum the RMS or MS of two noises?
> This is because RMS or MS is just a temporal average of the power of the noise. They can not represent the value of a noise in every moment. 
> 



### Noise model of semiconductor components

> [!FAQ] Why is transistor low pass?
> This is mainly because of the capacitance effect in the PN junction of the BJT

> [!FAQ] Why does the collector output noise current $\overline{i_c^2}$ in the BJT noise model only have **Shot** noise but no Flicker noise and Burst noise?
> Because the flicker noise and burst noise are too small compared to shot noise, so they're ignored in analysis for simplicity

> [!FAQ] Why is $C_\mu$ ignored in the BJT hybrid-$\pi$ noise model?
> Beacuse its effect on noise is too small. Notice that usually $C_\mu$ is not ignorable in the hybrid-$\pi$ model when operating signal analysis. 



### Noise Analysis


> [!FAQ] Why do we use a input equivalent noise current source and a input equivalent noise voltage source instead of just using one single equivalent noise source?
>


> [!FAQ] Why doesn't Noise Factor work on non-resistive $R_S$?
> That's because the internal resistance of a voltage source is always resistive. In fact, the Noise Factor only focuse on the power of signal and noise, not the impedence in the circuit. So it works on all circuit. 

### Tutorial 1-4






---
## Wideband Amplifier Design




---
### 💡 Random Thoughts


> [!TIP] Why do we care more about the noise **power** rather than its value?
> Contents
