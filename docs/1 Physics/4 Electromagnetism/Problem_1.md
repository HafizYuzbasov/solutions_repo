# Problem 1

Great! Based on the images you've shared and the task description, here's a full solution in Markdown format that includes code and explanation for simulating the motion of charged particles under different electric and magnetic field configurations, matching the visual style of the plots you provided.

---

# **Simulating the Effects of the Lorentz Force**

## **1. Applications of the Lorentz Force**

The Lorentz force,

$$
\mathbf{F} = q\mathbf{E} + q\mathbf{v} \times \mathbf{B},
$$

is fundamental in a range of physical systems:

* **Particle accelerators:** Control particle trajectories using electric and magnetic fields.
* **Mass spectrometers:** Separate ions based on mass-to-charge ratio via curved paths in magnetic fields.
* **Plasma confinement (tokamaks):** Magnetic fields trap charged particles, forming helical motion.
* **Cathode ray tubes:** Use E and B fields to steer electrons.

## **2. Simulating Particle Motion**

### **Equations of Motion**

For a particle of charge $q$ and mass $m$, Newton's second law gives:

$$
m\frac{d\mathbf{v}}{dt} = q(\mathbf{E} + \mathbf{v} \times \mathbf{B}).
$$

We'll use the **Runge-Kutta 4th order (RK4)** method to solve these differential equations.

### **Python Implementation**

```python
import numpy as np
import matplotlib.pyplot as plt
from mpl_toolkits.mplot3d import Axes3D

def lorentz_force(q, E, B, v):
    return q * (E + np.cross(v, B))

def rk4_step(x, v, dt, q, m, E, B):
    def acceleration(v):
        return lorentz_force(q, E, B, v) / m

    k1v = acceleration(v)
    k1x = v

    k2v = acceleration(v + 0.5 * dt * k1v)
    k2x = v + 0.5 * dt * k1v

    k3v = acceleration(v + 0.5 * dt * k2v)
    k3x = v + 0.5 * dt * k2v

    k4v = acceleration(v + dt * k3v)
    k4x = v + dt * k3v

    x_next = x + (dt / 6.0) * (k1x + 2*k2x + 2*k3x + k4x)
    v_next = v + (dt / 6.0) * (k1v + 2*k2v + 2*k3v + k4v)

    return x_next, v_next

def simulate_motion(E, B, v0, x0, q, m, steps, dt):
    positions = []
    velocities = []

    x = np.array(x0, dtype=float)
    v = np.array(v0, dtype=float)

    for _ in range(steps):
        positions.append(x.copy())
        velocities.append(v.copy())
        x, v = rk4_step(x, v, dt, q, m, E, B)

    return np.array(positions)

def plot_trajectory(positions, title):
    fig = plt.figure()
    ax = fig.add_subplot(111, projection='3d')
    ax.plot(positions[:,0], positions[:,1], positions[:,2])
    ax.set_xlabel('x (m)')
    ax.set_ylabel('y (m)')
    ax.set_zlabel('z (m)')
    ax.set_title(title)
    plt.show()
```

### **Scenarios**

#### **a) Uniform Magnetic Field (Circular Motion)**

```python
E = np.array([0, 0, 0])
B = np.array([0, 0, 1])  # 1 T along z
v0 = [1, 0, 0]           # initial velocity
x0 = [0, 0, 0]
positions = simulate_motion(E, B, v0, x0, q=1, m=1, steps=1000, dt=0.01)
plot_trajectory(positions, "Uniform Magnetic Field\n(B=1.0 T): Circular Motion")
```

#### **b) Parallel Electric and Magnetic Fields (Helical Motion)**

```python
E = np.array([0, 0, 0.5])
B = np.array([0, 0, 1])
v0 = [1, 0, 1]  # initial velocity has component along B
x0 = [0, 0, 0]
positions = simulate_motion(E, B, v0, x0, q=1, m=1, steps=1000, dt=0.01)
plot_trajectory(positions, "Parallel Electric & Magnetic Fields\n(E=0.5 V/m, B=1.0 T): Helical Motion")
```

#### **c) Crossed Electric and Magnetic Fields (Drift Motion)**

```python
E = np.array([0.5, 0, 0])
B = np.array([0, 0, 1])
v0 = [0, 1, 0]  # initial velocity
x0 = [0, 0, 0]
positions = simulate_motion(E, B, v0, x0, q=1, m=1, steps=1000, dt=0.01)
plot_trajectory(positions, "Crossed Electric & Magnetic Fields\n(E ⊥ B, E=0.5 V/m, B=1.0 T): Drift Motion")
```

## **3. Parameter Exploration**

Try adjusting:

* $B = 2.0$ T or $0.5$ T.
* $E = 1.0$ V/m or change direction.
* $v_0$: initial angles and speeds.
* $q$, $m$: like for an electron $q = -1.6 \times 10^{-19}$ C.

Observe:

* **Larmor radius:** $r = \frac{mv_{\perp}}{qB}$
* **Helical pitch:** $v_{\parallel} \cdot T$, where $T = \frac{2\pi m}{qB}$
* **Drift velocity:** $\mathbf{v}_d = \frac{\mathbf{E} \times \mathbf{B}}{B^2}$

## **4. Visualization Samples**

The resulting plots replicate the behavior seen in your images:

* **Circular motion** in a magnetic field.
* **Helical path** when $\mathbf{v}$ has a component along $\mathbf{B}$.
* **Drift motion** when $\mathbf{E} \perp \mathbf{B}$.

## **5. Extensions**

Future simulations could include:

* **Non-uniform magnetic fields** (e.g., magnetic mirrors).
* **Time-varying fields** (simulate induction).
* **Relativistic corrections** (for very fast particles).
* **Collisions in plasma simulations.**

---