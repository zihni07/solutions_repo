# 📚 Problem 1: Exploring the Central Limit Theorem through Simulations

## 🎯 Motivation

The **Central Limit Theorem (CLT)** is a fundamental result in probability and statistics.  
It states that the sampling distribution of the sample mean $\bar{X}$ approaches a **normal distribution** $N(\mu, \sigma^2/n)$ as the sample size $n$ increases, regardless of the shape of the original population distribution.

Simulations provide an intuitive, visual, and hands-on way to observe this phenomenon, deepening our understanding of the CLT.

---

## 🛠 Task Breakdown

### 1. Simulating Sampling Distributions

We will select several types of **population distributions**:

- **Uniform distribution** $ U(a, b) $
- **Exponential distribution** $ \text{Exp}(\lambda) $
- **Binomial distribution** $ \text{Bin}(n, p) $
- **Normal distribution** $ N(\mu, \sigma^2) $ (for control)

For each distribution:

- Generate a **large dataset** (population size $ \approx 10^5 $).

---

### 2. Sampling and Visualization

For each population:

- Randomly sample subsets of various sizes:  
  $n \in \{5, 10, 30, 50, 100\}$

- Repeat **1000** times to build the **sampling distribution** of $\bar{X}$.
- Visualize:
  - **Histograms** with **KDE** (Kernel Density Estimation) plots.
  - **QQ-plots** to check normality visually.

---

### 3. Parameter Exploration

Investigate:

- How the **sample size** $n$ affects convergence speed.
- How the **population shape** and **population variance** $\sigma^2$ influence the **spread** and **skewness** of the sampling distribution.

---

### 4. Practical Applications of the CLT

The Central Limit Theorem is crucial for:

- **Estimation**: Confidence intervals for population means.
- **Quality Control**: Monitoring production processes.
- **Finance**: Risk assessment and prediction models.
- **Machine Learning**: Model evaluation with cross-validation.

---

# 📄 Deliverables

- Well-structured **Markdown report**.
- **Python notebooks** or **scripts** implementing the simulations.
- **Plots** showcasing the evolution toward normality.
- **Discussion** explaining observations and theoretical justifications.

---

# 💡 Hints and Resources

- Use:
  - `numpy` for random sampling.
  - `matplotlib` and `seaborn` for visualization.
  - `scipy.stats.probplot` for QQ-plots.
- Start simple, progressively increase complexity.
- Always calculate and show:
  - Sample mean $\bar{X}$
  - Sample variance $S^2$

---

# 🧪 Python Simulation

## Import Required Libraries

```python
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import scipy.stats as stats

sns.set(style="whitegrid")
