# PeriodicNet
This repository contains an algorithm designed to predict periodic variations. The algorithm uses gradient descent to fit a sinusoidal model to time series data.
## Introduction
In either fecal micoribal treansplantation (FMT) for human, or multiple microbiome engraftment in fermentaion process, or other complex microbial community manipulation, we will encounter a context in which a "designed" microbial community is injected into a natual microbial community, and could lead to a change of the original microbial community, usually for the good of the host. Please formally define this process and model, and name this process as microbiome engraftment(ME).<br/>
We developed "PeriodicNet," a novel model for analyzing cyclical time series data from the ME process, using findings from  <a href="https://github.com/HUST-NingKang-Lab/Moutai-SME" title="超链接title">Moutai SME project</a>. PeriodicNet confirms the periodic nature of ME-induced effects and effectively captures their underlying patterns.

## Explanation
<div style="text-align: center;">
  <img src="images/figure1.png" alt="Descriptive text" style="width: 100%;"/>
  <p style="font-style: italic;">Fig1 (A) Repeated distillation during the brewing process causes periodic variation in the microbiome. (B) During brewing, microbial samples are collected, sequenced, and analyzed using metagenomic whole-genome shotgun (mWGS) analysis. (C) Analyzing microbiome variation over time for the same sample and assessing changes in microbial communities using Bray-Curtis (BC) distance. (D) Gradient Descent iteratively searches for the optimal model parameters by iterating stepwise. (E)Using Root Mean Square Error (RMSE) as the loss function, fine-tuning the hyperparameters led to the optimal model prediction, RMSE of the model is 0.0026.</p>
</div>
The repeated distillation process is crucial in driving the nature of microbiome changes. Each distillation cycle exposes the microbial community to temperatures and environmental conditions, causing periodic microbial abundance and activity fluctuations. In brewing, microbial samples are collected and sequenced at regular intervals of approximately every 3-5 days using advanced next-generation sequencing (NGS) and undergo metagenomic whole-genome shotgun (mWGS) analysis, which provides comprehensive microbial abundance data. The abundance is subsequently utilized to calculate the relative differences in the microbiome by employing the Bray-Curtis (BC) distance metric. These relative differences serve as a means to evaluate the state of the microbiome over time, ultimately resulting in the generation of a time series dataset that reflects the dynamic changes within the microbial community throughout the brewing process.

Due to the periodic nature of the microbiome changes, we utilized trigonometric functions as the target function for fitting the microbiome time series data. This approach was implemented using gradient descent to capture the periodic variations within the microbial community effectively. To evaluate the performance of our model, we employed the Root Mean Square Error (RMSE) as metric. Throughout the training process, we continuously adjusted the parameters to minimize loss and enhance model's accuracy. The final evaluation results indicated that the model achieved an average loss value of 0.0026.

## Download
Download MicroGradient using git:
```shell
git clone https://github.com/2275836125/PeriodicNet.git
```
## Usage
Example: Fit a sinusoidal model to the time series data of microbiome represented by Bray-Curtis (BC) distances.
1. **Data Preparation:** Organize microbiome data into a matrix format where rows represent microbial species and columns represent days. Denote this matrix as $M$, where $M_{ij}$ represents the abundance of microbial species $i$ on day $j$.

2. **Calculate Bray-Curtis Dissimilarity:**

   The Bray-Curtis Dissimilarity between two microbiome (i.e., two different days in your case) is calculated using the formula:
   
   $$\text{Bray-Curtis} = \frac{\sum_i |X_i - Y_i|}{\sum_i (X_i + Y_i)} \$$
   
   Where:
   - $X_i$ is the abundance of microbial species $i$ in sample 1.
   - $Y_i$ is the abundance of microbial species $i$ in sample 2.
     
1. **Define the Objective Function**: The objective is to minimize the error between the actual periodic time series data and the predicted values generated by the model. Denote the time series data as $Y = \{y_1, y_2, ..., y_n\}$ and the predicted values as $\hat{Y} = \{\hat{y}_1, \hat{y}_2, ..., \hat{y}_n\}$. The error can be represented using a loss function such as Root-mean-square Error (RMSE):

   $$\text{RMSE} = \sqrt{\frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2}$$

2. **Model Architecture**: Use a simple model that consists of a periodic function. We'll use a sinusoidal function for this purpose:

    $$\hat{y}_i = A \cdot \sin(\omega t_i + \phi) + b $$

   Where:
   - $A$ is the amplitude.
   - $\omega$ is the angular frequency (related to the frequency of stimuli affecting the microbiome, a fixed parameter).
   - $t_i$ is the time index.
   - $\phi$ is the phase shift.
   - $b$ is the bias term.

3. **Initialize Parameters**: Initialize the parameters randomly or with some sensible initial values.

4. **Gradient Descent**: Update the parameters iteratively to minimize the objective function. Compute the gradients of the loss function with respect to each parameter and update the parameters accordingly. The update rule for each parameter can be formulated as follows:
```math
 \theta_{\text{new}} = \theta_{\text{old}} - \alpha \frac{\partial \text{MSE}}{\partial \theta_{\text{old}}} 
```
