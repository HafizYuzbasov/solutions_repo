# PROBLEM 2

## 1. Theoretical Foundation

### The Forced Damped Pendulum Model

The motion of a forced damped pendulum can be described by the following second-order ordinary differential equation (ODE):

$$
\theta''(t) + 2 \gamma \theta'(t) + \omega_0^2 \theta(t) = F_0 \cos(\omega t)
$$

Where:

- \( \theta(t) \) is the angular displacement of the pendulum as a function of time,
- \( \gamma \) is the damping coefficient (representing the frictional or resistive forces),
- \( \omega_0 \) is the natural frequency of the pendulum (which depends on the length and acceleration due to gravity),
- \( F_0 \) is the amplitude of the external driving force,
- \( \omega \) is the driving angular frequency, and
- \( t \) is time.

This equation describes the motion of the pendulum under the influence of both damping and an external periodic force. The term \( 2 \gamma \theta'(t) \) represents the damping force, \( \omega_0^2 \theta(t) \) represents the restoring force due to gravity, and \( F_0 \cos(\omega t) \) is the periodic driving force.

### Small-Angle Approximation

For small oscillations, we can assume that the angle \( \theta(t) \) is small enough that \( \sin(\theta(t)) \approx \theta(t) \), simplifying the equation of motion to:

$$
\theta''(t) + 2 \gamma \theta'(t) + \omega_0^2 \theta(t) = F_0 \cos(\omega t)
$$

This is a standard forced damped harmonic oscillator equation, which is more analytically tractable. The solution to this equation depends on several factors, including the damping coefficient, driving frequency, and driving amplitude.

### Approximate Solution for the Forced Damped Pendulum

The general solution to the equation consists of two parts:

1. **Homogeneous Solution** (related to the system's natural dynamics without the external force):

   $$
   \theta_h(t) = A e^{-\gamma t} \cos(\omega_0 t + \phi)
   $$

   Where \( A \) and \( \phi \) are constants determined by initial conditions, and the exponential decay factor \( e^{-\gamma t} \) represents the damping of the system over time.

2. **Particular Solution** (due to the external driving force):

   For a steady-state solution, we assume the system reaches a constant amplitude oscillation due to the external force. This solution can be written as:

   $$
   \theta_p(t) = B \cos(\omega t - \delta)
   $$

   Where \( B \) is the amplitude of oscillation and \( \delta \) is the phase shift between the external force and the oscillation.

   Substituting this into the differential equation and solving for \( B \) and \( \delta \) gives us the particular solution:

   $$
   B = \frac{F_0}{\sqrt{(\omega_0^2 - \omega^2)^2 + (2 \gamma \omega)^2}}
   $$

   $$
   \delta = \tan^{-1}\left(\frac{2 \gamma \omega}{\omega_0^2 - \omega^2}\right)
   $$

Thus, the complete solution to the equation is:

$$
\theta(t) = A e^{-\gamma t} \cos(\omega_0 t + \phi) + \frac{F_0}{\sqrt{(\omega_0^2 - \omega^2)^2 + (2 \gamma \omega)^2}} \cos(\omega t - \delta)
$$

### Resonance Conditions and Energy Implications

Resonance occurs when the driving frequency \( \omega \) matches the natural frequency \( \omega_0 \) of the pendulum. At resonance, the amplitude of oscillation \( B \) becomes large because the denominator in the expression for \( B \) becomes very small. In practice, resonance results in the system absorbing maximum energy from the external driving force.

The energy absorbed by the system at resonance can be significant, and the oscillation amplitude grows, potentially leading to large motions. This behavior is especially important in engineering, where resonance must be avoided in structures like bridges and buildings to prevent catastrophic failure.

---

## 2. Analysis of Dynamics

### Influence of Damping Coefficient, Driving Amplitude, and Frequency

- **Damping Coefficient (\( \gamma \)):**
  - As \( \gamma \) increases, the system's oscillations decay more rapidly, reducing the amplitude of oscillation. High damping can suppress resonance effects, limiting the system's ability to oscillate at high amplitudes.
- **Driving Amplitude (\( F_0 \)):**
  - Increasing \( F_0 \) increases the amplitude of the system’s steady-state oscillations. However, at very high \( F_0 \), the system may exhibit nonlinear behavior, and the simple harmonic approximation may no longer be valid.
- **Driving Frequency (\( \omega \)):**
  - The driving frequency affects the resonance condition. If \( \omega \) is close to \( \omega_0 \), resonance occurs, and the amplitude of oscillations becomes large. Away from resonance, the amplitude decreases.

### Transition from Regular to Chaotic Motion

As the driving amplitude or frequency is varied, the system can transition from regular periodic oscillations to chaotic motion. This can be characterized by sensitivity to initial conditions, where small changes in initial displacement or velocity lead to dramatically different behavior over time. The transition to chaos can be studied using **bifurcation diagrams** and **Poincaré sections**.

---

## 3. Practical Applications

- **Energy Harvesting Devices:**
  The forced damped pendulum can be used in energy harvesting systems where periodic forces are used to extract energy. By tuning the system to resonate with the driving frequency, maximum energy transfer can occur.

- **Suspension Bridges:**
  In suspension bridges, oscillations can be driven by wind or traffic. The design must consider the possibility of resonance, which could lead to destructive oscillations.

- **Oscillating Circuits:**
  Driven RLC circuits, analogous to the forced damped pendulum, demonstrate similar behaviors. Engineers design circuits to avoid resonance to prevent excessive power consumption or damage.

---

## 4. Implementation

In order to explore these behaviors computationally, a numerical simulation is required. A Python script or Jupyter notebook can be used to simulate the motion of the forced damped pendulum using methods like **Runge-Kutta integration** for solving the differential equation numerically.

### Numerical Methods

The second-order differential equation can be transformed into a system of first-order differential equations:

$$
\theta'(t) = v(t)
$$

$$
v'(t) = -2 \gamma v(t) - \omega_0^2 \theta(t) + F_0 \cos(\omega t)
$$

Using a method like the **Runge-Kutta 4th order method**, we can integrate these equations over time and observe the system's behavior under different conditions.

### Phase Diagrams and Poincaré Sections

- **Phase Diagram:** Plot \( \theta(t) \) vs. \( v(t) \) (angular velocity), which shows the system’s trajectory in phase space.
- **Poincaré Section:** A plot of the system's state at periodic intervals (e.g., every time the pendulum passes through the equilibrium position) to visualize the onset of chaotic behavior.

---

## Deliverables

1. **Markdown Document:**

   - A detailed explanation of the theory and solution for the forced damped pendulum.
   - Discussion on resonance, chaotic behavior, and energy transfer.

2. **Python Code/Notebook:**

   - Python code to simulate the forced damped pendulum dynamics.
   - Graphical representations of motion, including resonance and chaotic behavior.

3. **Visualizations:**

   - Phase diagrams and Poincaré sections for different parameter settings (damping coefficient, driving amplitude, frequency).

4. **Discussion:**
   - Analysis of the limitations of the model, such as nonlinear damping, and suggestions for potential extensions (e.g., non-periodic forcing, multi-degree-of-freedom systems).

```python


import numpy as np
import matplotlib.pyplot as plt
from scipy.integrate import solve_ivp

# Constants
gamma = 0.1  # Damping coefficient
omega_0 = 2.0  # Natural frequency of the pendulum
F_0 = 1.0  # Driving force amplitude
omega = 1.8  # Driving frequency
t_span = (0, 50)  # Time span for simulation (start, end)
initial_conditions = [0.1, 0]  # Initial conditions: [theta(0), omega(0)]

# Define the system of differential equations
def forced_damped_pendulum(t, y):
    theta, omega = y
    dtheta_dt = omega
    domega_dt = -2 * gamma * omega - omega_0**2 * theta + F_0 * np.cos(omega * t)
    return [dtheta_dt, domega_dt]

# Solve the differential equation using the Runge-Kutta method
sol = solve_ivp(forced_damped_pendulum, t_span, initial_conditions, t_eval=np.linspace(t_span[0], t_span[1], 10000))

# Extract the solution
time = sol.t
theta = sol.y[0]
omega = sol.y[1]

# Plot the results

# Plot Angular Displacement vs Time
plt.figure(figsize=(12, 6))
plt.subplot(2, 2, 1)
plt.plot(time, theta, label="Angular Displacement (theta)")
plt.title("Angular Displacement vs Time")
plt.xlabel("Time [s]")
plt.ylabel("Theta [rad]")
plt.grid(True)

# Plot Angular Velocity vs Time
plt.subplot(2, 2, 2)
plt.plot(time, omega, label="Angular Velocity (omega)", color='orange')
plt.title("Angular Velocity vs Time")
plt.xlabel("Time [s]")
plt.ylabel("Omega [rad/s]")
plt.grid(True)

# Phase Plot (theta vs omega)
plt.subplot(2, 2, 3)
plt.plot(theta, omega, label="Phase Plot")
plt.title("Phase Plot (Theta vs Omega)")
plt.xlabel("Theta [rad]")
plt.ylabel("Omega [rad/s]")
plt.grid(True)

# Poincaré Section (plot at theta = 0)
poincare_section = theta[theta[:-1] * theta[1:] < 0]
poincare_omega = omega[:-1][theta[:-1] * theta[1:] < 0]

plt.subplot(2, 2, 4)
plt.plot(poincare_section, poincare_omega, 'o', label="Poincaré Section")
plt.title("Poincaré Section")
plt.xlabel("Theta [rad]")
plt.ylabel("Omega [rad/s]")
plt.grid(True)

# Show the plots
plt.tight_layout()
plt.show()

```

![alt text](image-2.png)
