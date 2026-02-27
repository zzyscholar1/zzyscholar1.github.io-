# A Deep Learning Approach to Probability of Shortfall in Defined Contribution Plan Optimization

## Overview

This project develops a **Neural Network (NN)** framework to determine the optimal decumulation strategy for retirees with **Defined Contribution (DC)** pension plans.

Instead of using **Expected Shortfall (ES)** as the risk measure, we reformulate the problem using **Probability of Shortfall (PS)** — the probability that terminal wealth falls below a predefined threshold.

Our objective:

> Maximize withdrawals while minimizing the probability of wealth depletion.

## Methodology

### 1. Problem Reformulation

The PS term involves a non-differentiable indicator function, which prevents gradient-based optimization using Monte Carlo simulation and stochastic gradient descent (SGD).

To address this:

* We approximate the indicator function using a **differentiable sigmoid function**
* This enables smooth backpropagation and stable NN training
* Final implementation uses sigmoid parameter: **ρ = 100**


### 2. Neural Network Training

We conduct extensive hyperparameter tuning:

* Learning rate
* Batch size
* Number of iterations
* Learning rate decay schedule


### 3. Benchmark Comparison

We compare NN results against a **PDE-based solution**, which serves as the benchmark for accuracy and reliability.


## Experiments & Analysis

* Control heat map analysis
* CDF comparison (κ = 7,000)
* Risk–withdrawal trade-off evaluation
* Out-of-sample testing on:

  * Synthetic data
  * Historical data
* Sensitivity analysis across economic conditions


## Key Findings

* The primary challenge is the **non-differentiability** of the indicator function.
* Replacing it with a sigmoid approximation enables effective optimization.
* With proper hyperparameter tuning, NN results closely match PDE solutions.
* The NN provides a computationally efficient alternative to PDE methods.

### Risk Measure Insight

* **Probability of Shortfall (PS)** is intuitive and directly measures depletion likelihood.
* However, PS does not capture the magnitude of the shortfall (unlike ES).
* Extending the framework to incorporate severity measures is left for future research.


## Conclusion

This study demonstrates that Neural Networks, combined with a differentiable approximation of Probability of Shortfall, can effectively optimize decumulation strategies in DC pension plans while achieving accuracy comparable to PDE-based approaches.
