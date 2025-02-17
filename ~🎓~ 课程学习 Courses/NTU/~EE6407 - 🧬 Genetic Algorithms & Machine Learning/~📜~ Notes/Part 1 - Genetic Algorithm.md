+ **Goal** - Obtain a good solution from the search space 
+ **Inspiration** - Evolution Theory (Those who fit survive)

+ [[#Problem Classification]]
	+ [[#Black Box Representation]]
	+ [[#Solution Search]]
	+ [[#Solution Requirement]]
	+ [[#P/NP Problems]]
+ [[#Genetic Algorithm Scheme and Concepts]] (IRPSV)
	+ [[#Individual]]
	+ [[#Representation]]
	+ [[#Population]]
	+ [[#Selection]]
	+ [[#Variation]]
+ [[#Genotype Representations and Variation Operators]]
	+ [[#Binary - Genetic Algorithm (GA)]]
	+ [[#Integer]]
	+ [[#Real-valued Vector - Evolution Strategies (ES)]]
	+ [[#Permutation]]
	+ [[#Tree - Genetic Programming (GP)]]
+ [[#Design Process]]
	+ [[#Stages]]
	+ [[#Check List]]
+ [[#Examples]]
	+ [[#Maximize Function Value]]
	+ [[#Eight Queens Problem]]
+ [[#Genetic Algorithms and Machine Learning]]


---
## Problem Classification 

The classification of problems is important in computer science and algorithm. 

### Black Box Representation

+ **Black Box Model** - three components: **Input, Model, Output**

All problems can be categorized under the scenario of a black box model. The type of a problem is determined by the **unknown** component, which represents the desired solution to the problem.

| Types        | Input       | Model       | Output      | Search Space   |
| ------------ | ----------- | ----------- | ----------- | -------------- |
| Optimization | **Unknown** | Known       | Known       | Large          |
| Modelling    | Known       | **Unknown** | Known       | Large          |
| Simulation   | Known       | Known       | **Unknown** | Small (Single) |

Moreover, modelling problems can be described as optimization problems. So technologically there's only two types of problems: **Optimization** & Simulation

### Solution Search

+ **Search Space** - All objects of interest, might include the desired solution

When finding a solution, the search space size determines the number of contents to search through. A large search space means a difficult and time-costly search.

Simulation problems are just direct computation, leading to the only solution. However, the optimization problem has a large search space.

### Solution Requirement 

Problems can also be categoried based on their solution requirements. There're two possible requirements that the acceptable solution must fulfill.

+ **Constraint** - Determined whether a solution is acceptable ("Above the line")
+ **Objective Funtion** - Defined a value that needs to be maximized ("Reach the peak")

| Constraints | Objective Function | Type                            | Abbre. |
| ----------- | ------------------ | ------------------------------- | ------ |
| Yes         | Yes                | Constraint Optimization Problem | COP    |
| Yes         | No                 | Constraint Satisfaction Problem | CSP    |
| No          | Yes                | Free Optimization Problem       | FOP    |

### P/NP Problems

+ P means **Polynomial Time** $O(n^k)$
+ NP means **Nondeterministic Polynomial Time**

The P/NP system classified problems based on the **worst-case time complexity** to find a solution to the problem.

+ **P** - a solution can be **found** and **verified** in $O(n^k)$ 
+ **NP** - a solution can be **verified** in $O(n^k)$, but may not be found in $O(n^k)$
+ **NP-Hard** - any **NP** problems can be **reduced** to this type in $O(n^k)$
+ **NP-Complete** - a solution can be **verified** in $O(n^k)$ and any **NP** problems can be **reduced** to this type in $O(n^k)$

The relationships between the four types

1. **P** is a subset of **NP**
2. **NP-Complete** is the intersection of **NP** and **NP-Hard**


![[Pasted image 20250215105717.png]]

+ **P=PN**? - If **one** NP-Complete problem can be solved in $O(n^k)$, then all the NP problem can be solved in $O(n^k)$ because the combination of reduction and solving can still be finished in $O(n^k)$, meaning that all the NP problems are actually P problems.

---
## Genetic Algorithm Scheme and Concepts


![[Pasted image 20250210142458.png]]

### Individual

Each individual in the genetic algorithm represents a potential solution which is also one of the items in the search space.

+ **Fitness** - Evaluated by a desired objective function. It determines how good the individual is and the possibility for it to survive the selection process.

+ **Phenotype** - The original interested property of an individual. 

+ **Genotype** - The encoded representation of an individual. The selection and variation of individuals are based on the genotype.

### Representation

Representation is the data type or structure used to encode the phenotype of individuals. It's the most significant component of a genetic algorithm as it explicitly affect the variation operations.

Some terms regarding the representation are borrowed from biology

+ **Chromosome** - the complete representation data of an individual 
+ **Gene** - a single value in the representation data

There're two types information in a chromosome no matter what representation data type is chosen. Different variations have different effect on the information.

+ **Adjacent Information** - how the genes are adjacent to each other
+ **Order Information** - the overall or partial sequence of genes

### Population

+ **Purpose** - maintain the diversity of survived individuals

Population is the size of the pool which contains all the survived individuals in the current generation (loop). The best individuals in the population pool is more likely to be chosen as parents of the next generation.

There are two types of population control model

+ **Generation** - individuals only survive for one generation, children replace old-guys completely
+ **Steady-state** - only eliminate the worst, best ones survive through generations

Population can be a constant or a variable.


### Selection

+ **Purpose** - improve quality (overall fitness) of the population

Selection chooses the good individuals and eliminates the bad based on their fitness. It happens before and after variation. 

Selection is based on weighted randomness rather than rank, meaning that the best is not always selected and the worst is not always rejected.

### Variation

+ **Purpose** - increase diversity to explore unknown regions of the search space 

Variation is the core process of the genetic algorithm as it produces new genotype and thus, potentially creating better individuals. 

Type of a variation is based on the number of inputs accepted by the variation operator.

+ **Mutation** - one input
+ **Recombination** - more than one input
	+ **Crossover** - two inputs
	+ **Multi-parent Recombination** - more than one inputs (not common)

Mutation usually only causes **small shift** in the search space, so it tends to exploit the regions that are already explored. It's the only way to **create new information**.

Recombination usually leads to **big jump** in the search space, so it's more explorative than exploitative. It's the only way to **pass down** current information.

> [!NOTE] Fun Fact
> Genetic algorithm can work with only **mutation** but not recombination.

---
## Genotype Representations and Variation Operators

The most significant stage in the design of a genetic algorithm is to find the suitable data type the represent the individuals. The representation data type determines the specific variation operators used in the algorithm.

Genetic Algorithm has many variants based on the data type used for representation

| Genetic Algorithm Variant     | Representation Data Type     |
| ----------------------------- | ---------------------------- |
| Genetic Algorithm (GA)        | binary string                |
| Evolution Strategies (ES)     | vector (real-valued)         |
| Evolutionary Programming (EP) | state (finite state machine) |
| Genetic Programming (GP)      | Lisp tree                    |

### Binary - Genetic Algorithm (GA)

+ **Encoding** - binary number
+ **Mutation** 
	+ **Random Bitwise Flip** - every bit has possibility $P$ to flip
+ **Crossover**
	+ **1-point** - randomly choose a position and exchange all the bits after it
	+ **N-point** - randomly choose $n$ positions and exchange only the bits between odd and even positions
	+ **Uniform**
		+ First offspring - first and last bits always exchange and every other bit has possibility $P$ to exchange
		+ Second offspring - bitwise inverse of the first offspring

![[Pasted image 20250214234219.png]]

### Integer

+ **Encoding** - integer string
+ **Mutation**
	+ **Creeping** - every gene has possibility $P$ to shift to a near value
	+ **Random Reset** - every gene has possibility $P$ changing to a random value
+ **Crossover** - (same as binary representation)

![[Pasted image 20250214234235.png]]

### Real-valued Vector - Evolution Strategies (ES)

+ **Encoding** - real-valued vector
+ **Mutation**
	+ **Uniform** - mutate a gene to a value sampled from a uniform distribution whose upper and lower bound is defined by the problem itself  
	+ **Gaussian** - randomly add a bias to a gene and the bias is sampled from a gaussian distribution with a zero average and a standard variance defined by the all the genes 
	+ **Self-adaptive** - just like gaussian, but the standard variance mutates first
+ **Crossover**
	+ **Arithmetic** - use the weighted average of allele genes from two parents as mutation value 
	+ **Blend**

![[Pasted image 20250215012117.png]]

### Permutation

+ **Encoding** - integer sequence
+ **Mutation**
	+ **Swap** - randomly choose two genes and exchange their position
	+ **Insert** - randomly choose two genes and move the second to the next position of the first 
	+ **Scramble** - randonly choose a subset of genes and randomly rearrage its sequence
	+ **Inversion** - randonly choose a subset of genes and invert its sequence
+ **Crossover** 
	+ **Order 1**
	+ **Partially Mapped (PMX)**
	+ **Cycle Crossover**
	+ **Edge**

![[Pasted image 20250215094815.png]]

### Tree - Genetic Programming (GP)

+ **Encoding** - tree
+ **Mutation** 
	+ **Random Subtree Replacement** - randomly select a position and subtitute its subtree
+ **Crossover** 
	+ **Random Subtree Exchange** - randomly select a position on both parents respectively and exchange the two subtrees

![[Pasted image 20250214234159.png]]

---
## Design Process

### Stages

Here are the stages to design a genetic algorithm

3. **Design the Representation** - choose a proper data form to represent the individuals
4. **Design the Variation Operators** - choose how individuals crossover or mutate based on the representation
	+ Balance mutation and recombination
	+ Change adjacent information vs change order information
5. **Assign the Population** - decide how many individuals a generation would have
	+ Constant population
	+ Variable population
6. **Design the Termination Condition** - decide when will the algorithm stop
	+ Generation-based
	+ Fitness-based
	+ Satisfaction-based
7. **Random Initialize the individuals and Start!**

### Check List

| Stuffs in GA                 | Your Design |
| ---------------------------- | ----------- |
| Solution (Phenotype)         |             |
| Representation (Genetype)    |             |
| Recombination Method         |             |
| Recombination Probability    |             |
| Mutation Method              |             |
| Mutation Probability         |             |
| Fitness (Objective Function) |             |
| Parent Selection Method      |             |
| Survival Selection Method    |             |
| Population Size              |             |
| Number of Parents            |             |
| Number of Offsprings         |             |
| Initialization Method        |             |
| Termination Condition        |             |

---
## Examples

### Maximize value from a Quadratic Function

| Stuffs in GA                 | Your Design                  |
| ---------------------------- | ---------------------------- |
| Solution (Phenotype)         | the integer variable $x$     |
| Representation (Genetype)    | binary number of $x$         |
| Recombination Method         | random uniform               |
| Recombination Probability    | 100%                         |
| Mutation Method              | random bitwise flip          |
| Mutation Probability         | 50%                          |
| Fitness (Objective Function) | $x^2$                        |
| Parent Selection Method      | random based on fitness      |
| Survival Selection Method    | random based on fitness      |
| Population Size              | 30                           |
| Number of Parents            | 2                            |
| Number of Offsprings         | 2                            |
| Initialization Method        | random                       |
| Termination Condition        | generation (loop) reach 1000 |

### Eight Queens Problem

| Stuffs in GA                 | Your Design                |
| ---------------------------- | -------------------------- |
| Solution (Phenotype)         | a pattern of queens        |
| Representation (Genetype)    | permutation                |
| Recombination Method         | 1-point switch             |
| Recombination Probability    | 100%                       |
| Mutation Method              | swap                       |
| Mutation Probability         | 80%                        |
| Fitness (Objective Function) | sum of possible checks     |
| Parent Selection Method      | choose the fittist five    |
| Survival Selection Method    | random based on fitness    |
| Population Size              | 100                        |
| Number of Parents            | 2                          |
| Number of Offsprings         | 2                          |
| Initialization Method        | random                     |
| Termination Condition        | find a zero check solution |


---
## Genetic Algorithms and Machine Learning

Although GA is considered a deprecated algorithm, it greatly inspires other machine learning algorithms.