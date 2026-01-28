# Assignment-2
<br>

# Learning Probability Density Functions using Data Only (GAN)
<br>

# 1. Objective
``` text The objective of this assignment is to learn an unknown probability density function (PDF) of a transformed random
 variable using a Generative Adversarial Network (GAN) without assuming any analytical or parametric distribution.
``` 
<br>

# 2. Dataset
``` text Dataset Name: India Air Quality Data
Feature Used: NO2 Concentration (x)
Source: Kaggle
Dataset Link: https://www.kaggle.com/datasets/shrutibhargava94/india-air-quality-data
```
<br>

# 3. Methodology
<br>

# Step 1: Data Transformation

``` text
Each value of NO2 concentration is transformed using the roll-number-based nonlinear function: z = x + ar _ sin(br _ x)
University Roll Number:
r = 102303729
```

# Computed Transformation Parameters
| Parameter | Formula                     | Value |
|----------|-----------------------------|-------|
| ar       | 0.5 × (r mod 7)             | 2.0   |
| br       | 0.3 × ((r mod 5) + 1)       | 0.9   |

# Final Transformation Function:
z = x + 2.0 _ sin(0.9 _ x)
<br>

# Step 2: PDF Estimation using GAN

``` text The transformed variable z is assumed to be sampled from an unknown distribution.
A Generative Adversarial Network (GAN) is designed and trained using only samples of z.
```
<br>

# Generator Architecture
``` text Input: Random noise sampled from N(0,1)
Layers:
  Linear 1 to 64 with ReLU
  Linear 64 to 128 with ReLU
  Linear 128 to 1
```
# Discriminator Architecture

```text Input: Real and generated z samples
Layers:
   Linear 1 to 128 with LeakyReLU
   Linear 128 to 64 with LeakyReLU
   Linear 64 to 1 with Sigmoid
```
<br>

# Working Principle:

```text The discriminator learns to classify real and fake samples.
The generator learns to produce realistic transformed samples.
```
<br>

# Step 3: PDF Approximation
```text 
After training the GAN:
A large number of synthetic samples were generated from the generator.
The probability density function was estimated using:
Histogram Density Estimation
Kernel Density Estimation (KDE)
```




