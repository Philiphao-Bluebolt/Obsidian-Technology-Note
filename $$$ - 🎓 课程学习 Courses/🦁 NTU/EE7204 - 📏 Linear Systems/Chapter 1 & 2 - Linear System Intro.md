The study of a physical system consists of three steps: Modeling, Analysis, and Design. The first step, modeling yields a ideal mathematical model of the real system by first principles or collected data. The obtained model is usually refered to as the **system**. 

+ **Theories**
	+ [System Types](#System%20Types)
	+ [System Descriptions](#System%20Descriptions)
	+ [Description Conversions](#Description%20Conversions)
	+ [Linearization of Nonlinear System](#Linearization%20of%20Nonlinear%20System)

+ **Examples**

+ [Questions](#Questions)
+ [Slides](#Slides)


---
## System Types

The system model can be categorized into different types based on the following properties

+ 🔀 [Numbers of Input and Output](#🔀%20Numbers%20of%20Input%20and%20Output) - Single-variable (SISO), Multi-variable (SIMO, MISO, MIMO)
+ 📐 [Continuity](#📐%20Continuity) - Continuous-Time (Analog, CTDV), Discrete-Time (Digital, Sampled)
+ 🎱 [Dynamicity](#🎱%20Dynamicity) - Dynamic, Static
+ ➡️ [Causality](#➡️%20Causality) - Causal, Acausal
+ 📏 [Linearity](#📏%20Linearity) - Linear, Nonlinear
+ 🧽 [Lumpedness](#🧽%20Lumpedness) - Lumped, Distributed
+ ⏰️ [Time Invariance](#⏰️%20Time%20Invariance) - Time-invariant (TI) <-> Time-varying (TV)


### 🔀 Numbers of Input and Output

A system may have different numbers of inputs and outputs. **Single-variable** systems only have one input and one output, thus also called Single Input Single Output (**SISO**) systems. **Multi-variable** systems may be **SIMO**, **MISO**, or **MIMO**, which are more complicated to analyze.

### 📐 Continuity

Continuity is the quality of receiving and generating continuous signal. Signals can be categoried into four types based on the continuity of the time (independent variable) and the value (dependent variable). 

|                   | Continuous-Time | Discrete-Time  |
| ----------------- | --------------- | -------------- |
| Continuous-Valued | Analog Signal   | Sampled Signal |
| Discrete-Valued   | CTDV Signal     | Digital Signal |

Usually, the continuity or discreteness of time is more important. **Continuous-time** systems receive and output continuous-time signal, while **discrete-time** systems receive and output discrete-time.

### 🎱 Dynamicity

Dynamicity is the quality of having memory. **Dynamic system** output not only depends on the current input, but also the past or future input and state, implying memory. **Static system** output only depends on the current input.

Dynamic systems are described as **sequential** in digital electronics while static systems are described as **combinational** or **memoryless**

### ➡️ Causality

Causality is the quality of being logically feasible. Outputs of **Acausal systems** relys on information of future states which is not allowed by the arrow of time, thus infeasible. **Causal system** output only depends on past or present state and input, thus feasible.

Static systems are always casual since their output only depends on current input.

### 📏 Linearity

Linearity is the quality of complying with the superposition properties, which means the addition and scalar multiplication applied to the input and output have the same effect.
$$\mathcal{L}(au_1+bu_2)=a\mathcal{L}(u_1)+b\mathcal{L}(u_2)$$
Strictly linear system doesn't exist in real world since most natural processes are highly nonlinear, but they're common in control engineering as a simplier approximation.

### 🧽 Lumpedness

Lumpedness refers to the finite dimension of a system model's states. If a system is **lumped**, it can be described by a finite number of state values or a vector of finite dimension. Otherwise it's **distributed** and requires infinite number of states to describe it, making it difficult to analyze.

The pure delay $y(t)=u(t-1)$ and the transmission line are the simpliest examples of distributed systems. 

### ⏰️ Time Invariance

Time-invariance is the quality of keeping the system parameters unchanged over time. Intuitively, time-invariant system 





---
## System Descriptions

A system can either be described as a blackbox model, neglecting all the inner states, or as a whitebox model, focusing on the states.

+ [Ordinary Differential Equation](#Ordinary%20Differential%20Equation)
+ [Polynomial Fraction Model](#Polynomial%20Fraction%20Model) (Transfer Function)
+ [State Space Model](#State%20Space%20Model)

### Ordinary Differential Equation




### Polynomial Fraction Model


### State Space Model

States are variables that represent the  of a system. 



---
## Description Conversions



### Controllible Canonical Form (CCF)


### Observable Canonical Form (OCF)


### State Space --> Transfer Function










---
## Linearization of Nonlinear System






---
## Questions

> **Why is the unit-delay system $y(t)=u(t-1)$ distributed?**


> 



---
## Slides

![](Lecture_1_2.pdf)