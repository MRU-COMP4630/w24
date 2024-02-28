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

# Learning from Experience

COMP 4630 | Winter 2024
Charlotte Curtis

---

## Overview
- Things that can go sideways, and how to mitigate them
- Transfer learning
- References and suggested reading:
    - [Scikit-learn book](https://librarysearch.mtroyal.ca/discovery/fulldisplay?context=L&vid=01MTROYAL_INST:02MTROYAL_INST&search_scope=MRULibrary&isFrbr=true&tab=MRULibraryResources&docid=alma9923265933604656): Chapter 11
    - [Deep Learning Book](https://www.deeplearningbook.org/): Chapter 8

---

## Revisiting Backpropagation
- For a network with $l$ layers, the gradients of the loss function with respect to the weights in the last layer are given by:
    $$\frac{\partial L}{\partial W^{(l)}} = \frac{\partial L}{\partial \hat{y}} \frac{\partial \hat{y}}{\partial f^{(l)}} \frac{\partial f^{(l)}}{\partial z^{(l)}} \frac{\partial z^{(l)}}{\partial W^{(l)}}$$
    
    assuming that the output $\hat{y} = f^{(l)}(z^{(l)})$ is a function of layer $l$'s input $z^{(l)} = W^{(l)} f^{(l-1)}(z^{(l-1)})$.
- At layer $l-1$, the gradients are computed as:
    $$\frac{\partial L}{\partial W^{(l-1)}} = \left(\frac{\partial L}{\partial \hat{y}} \frac{\partial \hat{y}}{\partial f^{(l)}} \frac{\partial f^{(l)}}{\partial z^{(l)}}\right) \frac{\partial z^{(l)}}{\partial f^{(l-1)}} \frac{\partial f^{(l-1)}}{\partial z^{(l-1)}} \frac{\partial z^{(l-1)}}{\partial W^{(l-1)}}$$

---

- At layer $l-2$, this becomes:
    $$\frac{\partial L}{\partial W^{(l-2)}} = \left(\frac{\partial L}{\partial \hat{y}} \frac{\partial \hat{y}}{\partial f^{(l)}} \frac{\partial f^{(l)}}{\partial z^{(l)}} \frac{\partial z^{(l)}}{\partial f^{(l-1)}} \frac{\partial f^{(l-1)}}{\partial z^{(l-1)}}\right) \frac{\partial z^{(l-1)}}{\partial f^{(l-2)}} \frac{\partial f^{(l-2)}}{\partial z^{(l-2)}} \frac{\partial z^{(l-2)}}{\partial W^{(l-2)}}$$

- And so on, until we reach the first layer.
- We are **recursively** applying the chain rule and re-using the gradients computed at the previous layer
- This is great for computational efficiency, but it can also lead to **vanishing** or **exploding gradients**
> :question: What happens when you multiply a number by a very small number many times? What about a very large number?

---

## Vanishing and Exploding Gradients
- **Vanishing/exploding gradients** are where the gradients become near zero or near infinity as they are propagated back through the network
- Particularly problematic for **recurrent** neural networks, where the same weights are multiplied by themselves repeatedly
- Also a problem for very deep networks, and part of the reason that deep learning was not popular until the 2010s
- :question: What changed?
- :question: Can you think of ways to mitigate these problems?

---

## The role of hidden activation functions
- In early works, the sigmoid or tanh functions were popular
- Both have a small range of non-zero gradients
- ReLU has a stable gradient for positive inputs, but can lead to the **dying ReLU** problem whereby certain neurons are "turned off"
- :question: How can we prevent dying ReLUs?

> Note: this may not be a problem, and ReLU is cheap. Don't optimize prematurely unless you're seeing lots of "dead" neurons.

---

## Initialization strategies
- Vanishing/exploding gradients can also be mitigated by careful initialization of the weights
- In 2010, [Glorot and Bengio](https://proceedings.mlr.press/v9/glorot10a.html) proposed the **Xavier** initialization for a layer with $m$ inputs and $n$ outputs:
    $$W_{i, j} \sim U\left(-\sqrt{\frac{6}{m + n}}, \sqrt{\frac{6}{m + n}}\right)$$
- Goal is to preserve the variance of the input and output in both directions
- Similar to LeCun initialization, and apparently an overlooked feature of networks from the 1990s
  
---

## Initialization for ReLU
- Glorot initialization was derived under the assumption of **linear** activation functions (even though they knew this wasn't the case)
- [He et al.](https://openaccess.thecvf.com/content_iccv_2015/html/He_Delving_Deep_into_ICCV_2015_paper.html) proposed the **He** initialization specifically for ReLU activations:
    $$W_{i, j} \sim N\left(0, \sqrt{\frac{2}{m}}\right)$$
- This can be defined in Keras as `kernel_initializer='he_normal'` or `kernel_initializer='he_uniform'`
- The choice of normal vs uniform is apparently not very important

---

## Batch normalization
- Also in 2015, [Ioffe and Szegedy](https://arxiv.org/abs/1502.03167) proposed **batch normalization** as a way to mitigate vanishing/exploding gradients
- This is simply a normalization **at each layer**, shifting and scaling the inputs to have a mean of 0 and a variance of 1 (across the batch)
- A **moving average** of the mean and variance is maintained during training, and used for normalization during inference
- It also ends up acting as **regularization**, magic!
- :question: Why wouldn't you want to use batch normalization?

---

## Transfer Learning
- All these little tricks are learned from the experience of others
- Wouldn't it be great if our **network** could do the same?
- **Transfer learning** basically copy pastes a trained network into a new task
- You can select which layers to keep, which to freeze, and which to re-train
- You can also drop new layers on top of the old ones
- Most of the time you want to freeze the early layers and add a new head
- :question: Why are the early layers more general?

---

<!-- 
_class: invert lead
_paginate: skip
 -->

## Next up: Time Series Data and Recurrent Neural Networks