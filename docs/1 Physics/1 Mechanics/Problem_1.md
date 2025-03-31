# Problem 1

# Investigating the Range as a Function of the Angle of Projection

## Theoretical Foundation

### Deriving the Governing Equations of Motion

To investigate the range as a function of the angle of projection, we begin by analyzing the motion of a projectile under the influence of gravity, assuming no air resistance. The governing equations of motion can be derived from Newton's second law of motion.

Consider the following:

1. **Horizontal Motion**: In the absence of horizontal forces, the horizontal velocity remains constant throughout the projectile’s flight.

   The horizontal displacement \( x(t) \) as a function of time \( t \) is given by:
   
   $$
   x(t) = v_0 \cos(\theta) \cdot t
   $$
   
   where:
   - \( v_0 \) is the initial velocity of the projectile
   - \( \theta \) is the angle of projection
   - \( t \) is the time elapsed
   
2. **Vertical Motion**: In the vertical direction, the only force acting is gravity. The vertical displacement \( y(t) \) is described by the second-order differential equation:
   
   $$
   \frac{d^2 y}{dt^2} = -g
   $$

   Integrating once gives the vertical velocity:

   $$
   \frac{dy}{dt} = v_0 \sin(\theta) - g \cdot t
   $$

   Integrating again to find the vertical displacement:

   $$
   y(t) = v_0 \sin(\theta) \cdot t - \frac{1}{2} g \cdot t^2
   $$

### Time of Flight

To find the time of flight, we solve for \( t \) when the projectile lands, i.e., when \( y(t) = 0 \). From the vertical displacement equation:

$$
v_0 \sin(\theta) \cdot t - \frac{1}{2} g \cdot t^2 = 0
$$

Factoring out \( t \), we get:

$$
t \left( v_0 \sin(\theta) - \frac{1}{2} g \cdot t \right) = 0
$$

The nontrivial solution is:

$$
t = \frac{2 v_0 \sin(\theta)}{g}
$$

Thus, the time of flight \( T \) is:

$$
T = \frac{2 v_0 \sin(\theta)}{g}
$$

### Horizontal Range

The horizontal range \( R \) is the horizontal distance the projectile travels during its flight. Using the time of flight, we can calculate \( R \):

$$
R = x(T) = v_0 \cos(\theta) \cdot T
$$

Substituting for \( T \):

$$
R = v_0 \cos(\theta) \cdot \frac{2 v_0 \sin(\theta)}{g}
$$

Simplifying:

$$
R = \frac{v_0^2 \sin(2\theta)}{g}
$$

### Variations in Initial Conditions

The range \( R \) depends on both the initial velocity \( v_0 \) and the angle of projection \( \theta \). By analyzing this equation, we can see how variations in these initial conditions lead to a family of solutions:

1. **Initial Velocity \( v_0 \)**: A higher initial velocity leads to a larger range. Specifically, the range increases with the square of the initial velocity, \( v_0^2 \).

2. **Angle of Projection \( \theta \)**: The term \( \sin(2\theta) \) in the
