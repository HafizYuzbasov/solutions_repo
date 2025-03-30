# Problem 1

# Simple Pendulum Experiment

## Abstract

This experiment aims to determine the acceleration due to gravity \( g \) by analyzing the motion of a simple pendulum. By carefully measuring the period of oscillation and accounting for uncertainties, we assess the precision of our results and identify sources of error.

## Procedure

### 1. Materials:

- A string (1 or 1.5 meters long).
- A small weight (e.g., bag of coins, bag of sugar, key chain) mounted on the string.
- Stopwatch (or smartphone timer).
- Ruler or measuring tape.

### 2. Setup:

- Attach the weight to the string and fix the other end to a sturdy support.
- Measure the length of the pendulum, \( L \), from the suspension point to the center of the weight using a ruler or measuring tape.
- Record the resolution of the measuring tool and calculate the uncertainty as half the resolution:  
  \( \Delta L = \frac{\text{Ruler Resolution}}{2} \).

### 3. Data Collection:

- Displace the pendulum slightly (<15°) and release it.
- Measure the time for 10 full oscillations (\( T\_{10} \)) and repeat this process 10 times. Record all 10 measurements.
- Calculate the mean time for 10 oscillations (\( \overline{T}\_{10} \)) and the standard deviation (\( \sigma_T \)).
- Determine the uncertainty in the mean time:  
  \( \Delta T\_{10} = \frac{\sigma_T}{\sqrt{10}} \).

## Calculations

### 1. Calculate the Period:

$$ T = \frac{\overline{T}_{10}}{10} $$
$$\Delta T = \frac{\Delta T_{10}}{10} $$

### 2. Determine \( g \):

$$g = \frac{4\pi^2 L}{T^2} $$

### 3. Propagate Uncertainties:

$$ \Delta g = g \sqrt{\left(\frac{\Delta L}{L}\right)^2 + \left(2 \frac{\Delta T}{T}\right)^2} $$

## Deliverables

### 1. Tabulated Data

| Quantity                      | Symbol                   | Value                                                                                  |
| ----------------------------- | ------------------------ | -------------------------------------------------------------------------------------- |
| Length of pendulum            | \( L \)                  | \( L \)                                                                                |
| Uncertainty in length         | \( \Delta L \)           | \( \frac{\text{Ruler Resolution}}{2} \)                                                |
| 10 oscillation times          | \( T\_{10} \)            | \( T*{10,1}, T*{10,2}, ..., T\_{10,10} \)                                              |
| Mean time for 10 oscillations | \( \overline{T}\_{10} \) | \( \frac{\sum T\_{10}}{10} \)                                                          |
| Standard deviation            | \( \sigma_T \)           | \( \sqrt{\frac{\sum (T*{10,i} - \overline{T}*{10})^2}{9}} \)                           |
| Uncertainty in mean time      | \( \Delta T\_{10} \)     | \( \frac{\sigma_T}{\sqrt{10}} \)                                                       |
| Period                        | \( T \)                  | \( \frac{\overline{T}\_{10}}{10} \)                                                    |
| Uncertainty in period         | \( \Delta T \)           | \( \frac{\Delta T\_{10}}{10} \)                                                        |
| Acceleration due to gravity   | \( g \)                  | \( \frac{4\pi^2 L}{T^2} \)                                                             |
| Uncertainty in \( g \)        | \( \Delta g \)           | \( g \sqrt{\left(\frac{\Delta L}{L}\right)^2 + \left(2 \frac{\Delta T}{T}\right)^2} \) |

### 2. Discussion on Uncertainty

- **Effect of measurement resolution on \( \Delta L \)**: The uncertainty in length measurement is determined by the resolution of the ruler. A higher resolution ruler would reduce \( \Delta L \), leading to a more precise value of \( g \).
- **Variability in timing and its impact on \( \Delta T \)**: Human reaction time affects stopwatch measurements, contributing to \( \sigma_T \). This, in turn, affects \( \Delta T \) and the uncertainty in \( g \).
- **Assumptions and experimental limitations**:
  - The small-angle approximation (\( \theta < 15^\circ \)) is assumed to ensure simple harmonic motion.
  - Air resistance and friction at the pivot are neglected, which may introduce small errors.
  - The string is assumed to be massless and inextensible.

## Conclusion

This experiment successfully estimates the acceleration due to gravity \( g \) using a simple pendulum. The precision of our results depends on the accuracy of our length and time measurements. While human reaction time introduces uncertainty, repeated measurements mitigate its effects. Future improvements include using automated timing systems and air resistance corrections for enhanced accuracy.
