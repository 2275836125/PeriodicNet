# MicroGradient

MicroGradient, a machine learning model based on gradient descent algorithm for prediction of trends in microbial genomes.

<div style="text-align: center;">
  <img src="images/figure1.png" alt="Descriptive text" style="width: 100%;"/>
  <p style="font-style: italic;">Fig1 (A) Baijiu making requires repeated distillation, during which the microbiome changes periodically (B)The microbiome was identified by 16s sequencing (C)Calculate differences of the microbiome (D)Gradient descent was used to optimise the model and RMSE is the loss function (E)Gradient descent to fit parameters</p>
</div>

## Explanation
Considering the cyclical nature of microbial changes in wine during distillation Fig.1(A), we wanted to predict changes in the microbiome. There are many approachs to quantify the dissimilarity between microbial communities, such as Euclidean Distance,Manhattan Distance,Jaccard Index,Bray-Curtis Dissimilarity,and they all worked well.Considering the periodicity of microbiome changes in distillation, we used a periodic function to predict microbiome changes Fig.1(E).RMSE is a common loss function used in regression problems. It measures the average magnitude of the errors between the predicted values and the actual values Fig.1(F). The model adopts the random initialization and the parameters were updated by gradient descent.

## Download
Download MicroGradient using git:
```shell
git clone https://github.com/2275836125/MicroGradient.git
```

## Usage
MicroGradient could predict trends of microbial genomes.The process involves some steps:

1. Obtain microbiome abundance data.
2. Calculation of correlation coefficients from microbiome abundance data.
3. Data preprocessing to conform data to input format.
4. Predict microbiome trends by MicroGradient.




