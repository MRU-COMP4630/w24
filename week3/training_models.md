---
marp: true
paginate: true
theme: marp-theme
math: true
---

<!-- 
_class: invert lead
_paginate: skip
 -->

# Training Models with Regression and Gradient Descent

COMP 4630 | Winter 2024
Charlotte Curtis

---

## Overview
- Linear Regression and the Normal Equation
    - Review of calculus and linear algebra
- Gradient Descent and its various flavours
- References and suggested reading:
    - [Scikit-learn book](https://librarysearch.mtroyal.ca/discovery/fulldisplay?context=L&vid=01MTROYAL_INST:02MTROYAL_INST&search_scope=MRULibrary&isFrbr=true&tab=MRULibraryResources&docid=alma9923265933604656):
        - Chapter 4: Training Models
    - [Deep Learning Book](https://www.deeplearningbook.org/)
        - Section 5.1.4: Linear Regression
    - [Understanding Deep Learning (UDL)](https://udlbook.github.io/udlbook/)
        - Chapter 2: Supervised Learning

---

## Linear Regression

Unlike most models, linear regression has a **closed-form** solution called the **Normal Equation**:

$$\mathbf{\hat{\theta}} = (\mathbf{X}^T \mathbf{X})^{-1} \mathbf{X}^T \mathbf{y}$$

where

- $\mathbf{\hat{\theta}}$ are the weights of the model minimizing the cost function
- $\mathbf{y}$ is the vector of target values
- $\mathbf{X}$ is the **design matrix** of feature values

Different sources use different notation! You will also see $\mathbf{w}$ or $\mathbf{\phi}$ instead of $\mathbf{\theta}$.


---

Consider the 1-d case:

![bg right:40% 120%](figs/noisy_line_plot.png)

$$\hat{y} = \theta_0 + \theta_1 x$$

we want the values of $\theta_0$ and $\theta_1$ that minimize the **Mean Square Error** between the actual and predicted $y$ values:

$$\begin{aligned}
MSE &= \frac{1}{m} \sum_{i=1}^m (\hat{y} - y_i)^2\\
MSE &= \frac{1}{m} \sum_{i=1}^m (\theta_0 + \theta_1 x_i - y_i)^2
\end{aligned}$$

<!-- y = mx + b -->

---

## A brief review of calculus
- A **partial derivative** is calculated by holding all other variables constant
- The derivative of the sum is the sum of the derivatives
    $$\frac{d}{dx} (f(x) + g(x)) = \frac{d}{dx} f(x) + \frac{d}{dx} g(x)$$

- The chain rule: 
    $$\frac{d}{dx} f(g(x)) = \frac{d}{dg} f(g) \cdot \frac{dg}{dx}$$

> :abacus: Find the partial derivative of the MSE with respect to $\theta_0$ and $\theta_1$

---

## Solving for $\theta_0$ and $\theta_1$

- The partial derivatives of the MSE with respect to $\theta_0$ and $\theta_1$ are:

$$\begin{aligned}
\frac{\partial}{\partial \theta_0} MSE &= \frac{2}{m} \sum_{i=1}^m (\theta_0 + \theta_1 x_i - y_i)\\
\frac{\partial}{\partial \theta_1} MSE &= \frac{2}{m} \sum_{i=1}^m (\theta_0 + \theta_1 x_i - y_i) x_i
\end{aligned}$$

- The minimum of the MSE occurs when the partial derivatives are zero, so we can directly solve for the optimum $\theta_0$ and $\theta_1$

---

## Solving for $\theta_0$ and $\theta_1$
![bg right:40% 120%](figs/best_fit_line.png)

After some algebraic gymnastics, we get:

$$\begin{aligned}
\theta_1 &= \frac{\mu_y \sum_{m}x_i - \sum_m x_i y_i}{\mu_x\sum_m x_i - \sum_m x_i^2}\\
\theta_0 &= \mu_y - \theta_1 \mu_x
\end{aligned}$$

where $\mu_x$ and $\mu_y$ are the means of the $x$ and $y$ values, respectively.

---

## A brief review of linear algebra
- A **vector** ($\mathbf{x}$) is a list of numbers assumed to be arranged in a **column**
- A **matrix** ($\mathbf{A}$) is a 2-d array of numbers

  $$\mathbf{x} = \begin{bmatrix} x_1 \\ x_2 \\ \vdots \\ x_n \end{bmatrix}, \hspace{1cm} \mathbf{A} = \begin{bmatrix} a_{11} & a_{12} & \cdots & a_{1n} \\ a_{21} & a_{22} & \cdots & a_{2n} \\ \vdots & \vdots & \ddots & \vdots \\ a_{m1} & a_{m2} & \cdots & a_{mn} \end{bmatrix}$$

---

## Matrix Product

![bg right:40% 120%](figs/Matrix_multiplication_diagram_2.svg)

- The **matrix product** of $\mathbf{A}$ and $\mathbf{B}$ is:

    $$\mathbf{C} = \mathbf{A} \mathbf{B}$$

    where the number of *columns* in $\mathbf{A}$ must equal the number of *rows* in $\mathbf{B}$

- Each element in $\mathbf{C}$ is given as:

    $$\mathbf{C}_{ij} = \sum_k \mathbf{A}_{ik} \mathbf{B}_{kj}$$

- Caution: $\mathbf{A} \mathbf{B} \neq \mathbf{B} \mathbf{A}$

<footer><a href="https://commons.wikimedia.org/wiki/File:Matrix_multiplication_diagram_2.svg">Image Source</a></footer>

---

## Transpose and Inverse

- The **transpose** of a matrix $\mathbf{A}$ or vector $\mathbf{x}$ is denoted with $^T$ and has its rows and columns flipped:
  
    $$\mathbf{A}^T_{ij} = \mathbf{A}_{ji}$$

- The matrix product of a vector $\mathbf{x}^T$ and another vector $\mathbf{y}$ is the **dot product**:

    $$\mathbf{x}^T \mathbf{y} = \sum_i x_i y_i$$

- The **inverse** of a *square* matrix $\mathbf{A}$ is denoted with $^{-1}$ and has the property:

    $$\mathbf{A} \mathbf{A}^{-1} = \mathbf{A}^{-1} \mathbf{A} = \mathbf{I}$$

    where $\mathbf{I}$ is the **identity matrix**.

---

## Properties of matrices and their transpose

The following properties are useful for solving linear algebra problems:

- $\mathbf{(AB)}^T = \mathbf{B}^T \mathbf{A}^T$

- $\mathbf{(A + B)}^T = \mathbf{A}^T + \mathbf{B}^T$

- $\mathbf{(A^{-1})}^T = (\mathbf{A}^T)^{-1}$

- $\mathbf{(A^T)}^T = \mathbf{A}$

Additionally, any matrix or vector multiplied by $\mathbf{I}$ is unchanged.

---

## Algebra with Matrices

Given a system of equations:

$$\mathbf{Ax} = \mathbf{b}$$

where $\mathbf{A}$ and $\mathbf{b}$ are known, solve for $\mathbf{x}$.

Assumptions:
- $\mathbf{A}$ is square and invertible
- $\mathbf{b}$ is a column vector

---

## The Gradient

The **gradient** of a function $f(x_1, x_2, \ldots, x_n)$ or vector $\mathbf{f}(\mathbf{x})$ is the vector of partial derivatives:

$$\nabla f = \begin{bmatrix} \frac{\partial f}{\partial x_1} \\ \frac{\partial f}{\partial x_2} \\ \vdots \\ \frac{\partial f}{\partial x_n} \end{bmatrix}$$

---

## The Design Matrix
Instead of the scalar $x$ or even vector $\mathbf{x}$, we can use a **design matrix** $\mathbf{X}$ to represent the feature values:

$$\mathbf{X} = \begin{bmatrix} x_{11} & x_{12} & \cdots & x_{1n} \\ x_{21} & x_{22} & \cdots & x_{2n} \\ \vdots & \vdots & \ddots & \vdots \\ x_{m1} & x_{m2} & \cdots & x_{mn} \end{bmatrix}$$

where each row is an instance (sample) and each column is a feature.

> It is common for the first column to be all ones, representing the bias term (the $b$ in $y = mx + b$).

<!-- What is the meaning of yhat being a vector? -->

---

## Back to the linear regression problem...
- We can rewrite the estimate in matrix notation:

$$\hat{\mathbf{y}} = \mathbf{X} \mathbf{\theta}$$

- The MSE can be written as:

    $$MSE = \frac{1}{m}\sum_{i=1}^m (\hat{y}_i - y_i)^2 = \frac{1}{m} (\mathbf{X} \mathbf{\theta} - \mathbf{y})^T (\mathbf{X} \mathbf{\theta} - \mathbf{y})$$

    where we've used the trick of substituting $\mathbf{a}^T \mathbf{a} = \sum_i a_i^2$

- :abacus: Find the gradient of the MSE w.r.t $\mathbf{\theta}$, set it to zero, and solve for $\mathbf{\theta}$

---

## The Normal Equation

We made it! The **Normal Equation** is again:

$$\mathbf{\hat{\theta}} = (\mathbf{X}^T \mathbf{X})^{-1} \mathbf{X}^T \mathbf{y}$$

- No optimization is required to find the optimal $\mathbf{\theta}$
- Limitations:
    - $\mathbf{X}^T \mathbf{X}$ must be invertible and small enough to fit in memory
    - The computational complexity is $O(n^3)$
- Even in linear regression problems, it is common to use **gradient descent** instead due to these limitations

---

## Gradient Descent
The goal of gradient descent is still to minimize the cost function, but it follows an iterative process:
1. Start with a random $\mathbf{\theta}$
2. Calculate the gradient $\nabla_{\mathbf{\theta}}$ for the current $\mathbf{\theta}$
3. Update $\mathbf{\theta}$ as $\mathbf{\theta} = \mathbf{\theta} - \eta \nabla_{\mathbf{\theta}}$
4. Repeat 2-3 until some stopping criterion is met

where $\eta$ is the **learning rate**, or the size of step to take in the direction opposite the gradient.

<!-- Draw a gradient on the board and illustrate steps -->

---

## Stochastic Gradient Descent
- Standard or **batch** gradient descent uses the entire training set to calculate the gradient for each instance at every step
- **Stochastic Gradient Descent** uses a single random instance at each step:
    1. Start with a random $\mathbf{\theta}$
    2. Pick a random instance $\mathbf{x}_i$ (row in the design matrix)
    3. Calculate the gradient $\nabla_{\mathbf{\theta}}$ for the current $\mathbf{\theta}$ and $\mathbf{x}_i$
    4. Update $\mathbf{\theta}$ as $\mathbf{\theta} = \mathbf{\theta} - \eta \nabla_{\mathbf{\theta}}$
    5. Repeat 2-4 until some stopping criterion is met

---

## Mini-batch Gradient Descent
![bg right:40% 110%](figs/gradient_descent_comparison.png)
- **Mini-batch** gradient descent uses a random *subset* of the training set
- Less chaotic than stochastic, but faster than batch
- Most common type of gradient descent used in practice

---

## Gradient Descent Hyper-parameters
- The **learning rate** $\eta$ - size of step taken
- No rule that it needs to be constant! A simple **learning schedule** is to decrease $\eta$ over time, e.g.:
    $$\eta = \frac{t_0}{t + t_1}$$
    where $t$ is the current iteration and $t_0$ and $t_1$ are hyper-parameters
- For mini-batch, the **batch size** is another hyper-parameter
- The number of **epochs**, or times to process the entire training set

---

## Stopping Criteria
![bg right:40% 110%](figs/early_stopping.png)
- The simplest stopping criterion is to set a maximum number of epochs
- **Early stopping** is another option:
    - Evaluate on a validation set at regular intervals
    - Stop when the validation error starts to increase
- The comparison between training and validation performance can also help prevent **overfitting**

---

## Loss functions
- The **loss function** is the function being minimized by gradient descent
- MSE is **convex** and guaranteed to have a single global minimum, but many other loss functions have multiple local minima
- The relative scale of the features can affect the convergence:

![h:200 center](figs/feature_scaling.png)

<footer>Figure from Scikit-Learn book</footer>

---

## Higher-order Polynomials
![bg right:35% fit](https://imgs.xkcd.com/comics/curve_fitting.png)
- Higher order polynomials can be solved with the Normal Equation as well:
  $$y = \theta_0 + \theta_1 x + \theta_2 x^2 + \cdots + \theta_n x^n$$
- Just include the higher order terms in $\mathbf{X}$
- This is still a linear regression problem because the coefficients are linear!
- Risk of **overfitting** the data
- Easy way to regularize: drop one or more of the higher order terms

---

## Regularization
- If the model fits the training data *too* well, but doesn't generalize to new data, it is **overfitting**
- Regularization imposes additional constraints on the weights
- Example: **Ridge Regression** adds a term to the loss function:
    $$J(\mathbf{\theta}) = MSE(\mathbf{\theta}) + \alpha \frac{1}{2} \sum_{i=1}^n \theta_i^2$$
    where $\alpha$ is the **regularization parameter**
- The regularization term is only added during training, not evaluation
> Note: the term **cost** function is often used instead of **loss** function

---

## Logistic regression and beyond
Logistic regression is a binary classifier that uses the **logistic function** (aka **sigmoid function**) to map the output to a range of 0 to 1:

$$\sigma(t) = \frac{1}{1 + e^{-t}}$$

resulting in the loss function (trust me on this one):

$$J(\mathbf{\theta}) = -\frac{1}{m} \sum_{i=1}^m \left[ y_i \log(\hat{p}_i) + (1 - y_i) \log(1 - \hat{p}_i) \right]$$

where $\hat{p}_i = \sigma(\mathbf{\theta}^T \mathbf{x}_i)$ is the probability that instance $i$ is positive.

---

The gradient of the loss function for logistic regression is given as:

$$\nabla_{\mathbf{\theta}} J(\mathbf{\theta}) = \frac{1}{m} \sum_{i=1}^m \left( \sigma(\mathbf{\theta}^T \mathbf{x}_i) - y_i \right) \mathbf{x}_i$$

- There is no (known) analytical solution this time, but we can still use gradient descent!
- In this case it's still convex, so we don't have to worry about local minima
- In general, for a loss function to work with gradient descent, it must be:
    - **Continuous** and
    - **Differentiable**
    - ... at the locations where you evaluate it

---

<!-- _class: lead invert -->

# Next up: Backpropagation! 