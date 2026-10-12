<div align="center">

# Monte Carlo Simulation for Uncertainty Analysis

### Propagating mixed probability distributions through a nonlinear function

[![Duke](https://img.shields.io/badge/Duke-CEE%20251L-00539B?style=flat-square)](#about)
[![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)](#run)
[![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=flat-square&logo=jupyter&logoColor=white)](Intro_Monte-Carlo_Simulation_Analysis.ipynb)

</div>

---

A compact example of Monte Carlo simulation: three random inputs with different distributions pass through a nonlinear function, and the probability of an outcome is estimated directly from the samples. It is a Python adaptation of the introductory example Prof. H. P. Gavin uses in CEE 251L at Duke.

## Problem

Estimate the probability that

$$
Y = \sin(X_1) + \sqrt{X_2} - e^{-X_3} - 2
$$

exceeds zero, where

| Input | Distribution |
|---|---|
| $X_1$ | Normal, mean 6, standard deviation 2 |
| $X_2$ | Lognormal, median 2, coefficient of variation 0.3 |
| $X_3$ | Rayleigh, $\sigma = 1$ |

## Method

1. Draw $N = 1000$ independent samples of each input.
2. Evaluate $Y^{(i)}$ for every sample.
3. Estimate the exceedance probability as the fraction of positive outcomes:

$$
\widehat{P}(Y > 0) = \frac{1}{N} \sum_{i=1}^{N} \mathbf{1}\{Y^{(i)} > 0\}
$$

4. Plot histograms and empirical CDFs of the inputs and of $Y$.

Sample, evaluate, aggregate: the same three steps scale to any model whose output can be computed but not derived in closed form.

## Run

```bash
pip install numpy scipy matplotlib jupyter
jupyter notebook Intro_Monte-Carlo_Simulation_Analysis.ipynb
```

## About

Adapted from `MCS_intro.m` by Prof. H. P. Gavin, Department of Civil and Environmental Engineering, Duke University (CEE 251L, Uncertainty, Design, and Optimization). Lognormal parameters are converted from median and coefficient of variation with the standard formulas used in the course.
