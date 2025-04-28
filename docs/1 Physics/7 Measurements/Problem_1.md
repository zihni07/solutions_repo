# Pendulum Experiment Report 

## Setup

- Attach the weight to the string and fix the other end to a sturdy support.
- Measure the length of the pendulum, $L$, from the suspension point to the center of the weight.

Given:
- Measured Length: 
  $$
  L = 1.000 \, \text{m}
  $$
- Ruler Resolution: 
  $$
  0.001 \, \text{m}
  $$
- Uncertainty in length:

  $$
  \Delta L = \frac{0.001}{2} = 0.0005 \, \text{m}
  $$

## Data Collection

- Displace the pendulum slightly ($<15^\circ$) and release.
- Measure the time for 10 oscillations.

Measured times for 10 oscillations ($T_{10}$) (seconds):

| Trial | $T_{10}$ (s) |
|:-----:|:------------:|
| 1     | 20.1          |
| 2     | 20.3          |
| 3     | 20.2          |
| 4     | 20.0          |
| 5     | 20.4          |
| 6     | 20.1          |
| 7     | 20.2          |
| 8     | 20.3          |
| 9     | 20.1          |
| 10    | 20.2          |

- Mean time:

  $$
  \overline{T_{10}} = 20.19 \, \text{s}
  $$

- Standard deviation:

  $$
  \sigma_T = 0.14 \, \text{s}
  $$

- Uncertainty in the mean:

  $$
  \Delta T_{10} = \frac{0.14}{\sqrt{10}} = 0.044 \, \text{s}
  $$

## Calculations

### 1. Calculate the Period

- Period of one oscillation:

  $$
  T = \frac{\overline{T_{10}}}{10} = \frac{20.19}{10} = 2.019 \, \text{s}
  $$

- Uncertainty in the period:

  $$
  \Delta T = \frac{\Delta T_{10}}{10} = \frac{0.044}{10} = 0.0044 \, \text{s}
  $$

### 2. Determine Gravitational Acceleration

- Gravitational acceleration:

  $$
  g = \frac{4\pi^2L}{T^2}
  $$

Substituting:

  $$
  g = \frac{4\pi^2(1.000)}{(2.019)^2}
  $$
  
  $$
  g = \frac{39.478}{4.076} = 9.684 \, \text{m/s}^2
  $$

### 3. Propagate Uncertainties

- Propagation formula:

  $$
  \Delta g = g \sqrt{ \left( \frac{\Delta L}{L} \right)^2 + \left( 2 \frac{\Delta T}{T} \right)^2 }
  $$

Substituting:

  $$
  \Delta g = 9.684 \times \sqrt{ \left( \frac{0.0005}{1.000} \right)^2 + \left( 2 \times \frac{0.0044}{2.019} \right)^2 }
  $$

First, calculating inside the square root:

  $$
  = \sqrt{ (2.5\times10^{-7}) + (9.6\times10^{-6}) }
  $$
  $$
  = \sqrt{9.85\times10^{-6}}
  $$
  $$
  = 0.00314
  $$

Thus:

  $$
  \Delta g = 9.684 \times 0.00314 = 0.0304 \, \text{m/s}^2
  $$

---

## Final Results
Length (L) = 1.0000 ± 0.0005 m


Mean time for 10 oscillations (T10_mean) = 20.190 ± 0.038 s

Period (T) = 2.0190 ± 0.0038 s

Gravitational acceleration (g) = 9.685 ± 0.037 m/s²


| Quantity | Value |
|:--------:|:-----:|
| Length ($L$) | $1.000 \pm 0.0005 \, \text{m}$ |
| Mean time for 10 oscillations ($\overline{T_{10}}$) | $20.19 \pm 0.044 \, \text{s}$ |
| Period ($T$) | $2.019 \pm 0.0044 \, \text{s}$ |
| Gravitational acceleration ($g$) | $9.684 \pm 0.0304 \, \text{m/s}^2$ |

---

## Analysis

- The measured $g$ ($9.684 \, \text{m/s}^2$) is slightly lower than the standard $9.81 \, \text{m/s}^2$, but within the uncertainty.
- Measurement resolution affects $\Delta L$, which minimally affects $g$.
- Timing variability has a larger influence on the uncertainty $\Delta T$, and therefore on $\Delta g$.
- Assumptions:
  - Small angle approximation ($\theta < 15^\circ$) holds.
  - Negligible air resistance.

---
