+ [Data Types](#Data%20Types)
+ [Categorical Analysis](#Categorical%20Analysis)
+ [Numerical Anaysis](#Numerical%20Anaysis)
	+ [Central Tendency and Dispersion](#Central%20Tendency%20and%20Dispersion)
	+ [Data Position and Box Plot](#Data%20Position%20and%20Box%20Plot)
	+ [Histogram](#Histogram)
+ [Inter-variable Analysis](#Inter-variable%20Analysis)
	+ [Scatter plot](#Scatter%20plot)
	+ [Two-way Cross-tabulation](#Two-way%20Cross-tabulation)
+ [Data Preprocessing](#Data%20Preprocessing)
	+ [Remediation](#Remediation)
	+ [Feature Scaling](#Feature%20Scaling)
	+ [Normalization and Standardization](#Normalization%20and%20Standardization)
	+ [Dimension Reduction and Feature Selection](#Dimension%20Reduction%20and%20Feature%20Selection)

---
## Data Types

The data features can be divided into two types: categorical and quantitative 

+ **Categorical (Qualitative)** - discretized and unmeasurable labels
	+ **Nominal** - non-sequential (nationality, brand, location)
	+ **Ordinal** - intrinsically sequential (grade, degree, criterion)
+ **Quantitative** - measurable values 
	+ **Interval** - ratio of values are meaningless since the zero point doesn't mean none
	+ **Ratio** - both difference (addition and subtraction) and ratio (multiplication and division) are meaningful since the zero point

The following table intuitively describes the properties of four data types. Sometimes, the data types at the right can be treated as the ones at its left. For example, if a interval or ratio data has few possible values, it can be treated as a ordinal data.

![](Pasted%20image%2020250505120521.png)

---
## Categorical Analysis

Since categorical data has no quantitative meaning, there's very few criterion to describe them. We can only focuse on the appearance of values.

> **Mode** - the most frequent value

> **Number of Unique Value** 
 
---
## Numerical Anaysis

Numerical data contains abundant information such as mean or variance which are absent from categorical data. We mainly focuse on the three aspects:

+ **Central Tendency**
+ **Dispersion**
+ **Sample Position**

### Central Tendency and Dispersion

+ **Goal** - uncover the data's **frequency** and **value** trend and how **scattered** it is 

> **Mean** - the average of all samples, consider both frequency (weight) and value and easily affected by outliers
$$E(x)=\bar{x}=\frac{1}{n}\sum_{i=1}^nx_i$$
> **Median** - the middle sample of sorted data, consider almost only value and thus not affected by outliers 

> **Mode** - the most frequent value, consider only the frequency

> **Variance** - the average of square distance from each sample to the data mean
$$\mathrm{var}=\sigma^2=\frac{1}{n}\sum_{i=1}^nx_i^2-\bar{x}^2=E(x^2)-E(x)^2$$
> **Standard Deviation** - the square root of variance
$$\sigma=\sqrt{\sigma^2}$$
### Data Position and Box Plot

 + **Goal** - describe and visualize the value distribution property of four sections in the data 

Box plot features the quartiles and outliers of the numerical data. It consists of the following parts: a box, two whiskers and marked outliers

+ **Box** - bounded by $Q_1$ and $Q_3$, with median $Q_2$ marked as a line
+ **Whiskers**
	+ Upper Whisker - bounded by non-outlier minimum and $Q_1$
	+ Lower Whisker - bounded by $Q_3$ and non-outlier maximum
+ **Outliers** - above $Q_3$ by $1.5(Q_3-Q_1)$ or below $Q_1$ by $1.5(Q_3-Q_1)$

![](Pasted%20image%2020250505211251.png)

> **Q3** - the **median** of the data subset (rank 75%) of samples **larger** the median (Q2) value

> **Median (Q2)** - the median of the data (rank 50%)

> **Q1** - the **median** of the data subset (rank 25%) of samples **smaller** the median (Q2) value

### Histogram

+ **Goal** - describe the value distribution of data

Histogram portrays the number of data samples by intervals (bins) and thus visually demonstrates the position distribution bias and clustering patterns of the data.

![](Pasted%20image%2020250505211926.png)

---
## Inter-variable Analysis

### Scatter Plot

Scatter plot features 


### Two-way Cross-tabulation




---
## Data Preprocessing


### Remediation


### Feature Scaling


### Normalization and Standardization


### Dimension Reduction and Feature Selection
