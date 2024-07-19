# Physics Informed Neural Network (PINN)

#
## Neural Networks

![Deep Neural Network Image ](https://eu-images.contentstack.com/v3/assets/blt6b0f74e5591baa03/blt790f1b7ac4e04301/6543ff50fcf447040a6b8dc7/News_Image_(47).png?width=850&auto=webp&quality=95&format=jpg&disable=upscale)

Neural Networks - Universal Function Predictors


## Our Goal - Solve a PDE

The question we have to solve here is:

$$
 \dfrac{d^2 f}{d x^2} = -f
$$

with the initial conditions:

$$
f(0) = 0 \quad , \quad \dfrac{d f}{d x}(0) = 1
$$




## Why can't we use a NN


> We are only given the PDE, nothing else. We don't have input and output data


## PINN

We need to make a few changes in Loss function to solve any PDE without any data.

The loss function for the PINN can be represented mathematically as:

$$
LOSS = (PDE)^2 + ( Initial-conditions-difference)^2
$$

## Loss Function

The loss function is defined as follows:

$$
\text{Loss} = \text{mean}\left(\left(\frac{d^2 f}{dx^2} + f\right)^2\right) + (f(0) - 0)^2 + \left(\frac{df}{dx}(0) - 1\right)^2 
$$

### Explanation

This loss function consists of three components:

1. **Mean Squared Error of the Differential Equation:**

$$
    \text{mean}\left(\left(\frac{d^2 f}{dx^2} + f\right)^2\right)    
$$

This term ensures that the function \( f \) satisfies the differential equation \( \frac{d^2 f}{dx^2} + f = 0 \).

2. **Boundary Condition at \( x = 0 \):**

$$
    (f(0) - 0)^2
$$

This term ensures that the function \( f \) satisfies the boundary condition \( f(0) = 0 \).

3. **Derivative Condition at \( x = 0 \):**

$$
    \left(\frac{df}{dx}(0) - 1\right)^2
$$

This term ensures that the derivative of \( f \) satisfies the condition \( \frac{df}{dx}(0) = 1 \).

### Usage

To implement this loss function in your code, you need to compute the second derivative of the function \( f \), evaluate the boundary and derivative conditions at \( x = 0 \), and then sum the three components.


where:
- $\frac{d^2 f}{dt^2}$ is the second derivative of $f$ with respect to time,
- $f$ is the function we are trying to approximate,
- $f(0)$ is the value of $f$ at the initial time,
- $\frac{df}{dt}(0)$ is the derivative of $f$ with respect to time at the initial time,
- $\text{mean}(\cdot)$ calculates the mean value across all data points.

This equation captures the squared L2 norm of the residual of the differential equation, along with penalties for the initial conditions.

This has the following exact solution:

$$
f(x) = sin(x)
$$




