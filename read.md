# MicroGradient

MicroGradient, a machine learning model based on gradient descent algorithm for prediction of trends in microbial genomes.

![Figure1](images/figure1.png?raw=true "figure1")
## Explanation
When making distilled spirits, multiple distillations are usually performed to purify the alcohol concentration. Considering the effects of repeated distillations, the microbiome of distilled spirit shows periodic changes with distillation.
The wine was sampled uninterruptedly during the 160-day distillation process. Abundance data of microorganisms of wine were obtained from the samples and correlation coefficients were calculated between them. The correlation coefficients give a more obvious picture of the periodic changes in the microbiome.
MicroGradient was fitted to the microbiome changes by the gradient descent algorithm to predict the trend of their correlation coefficients.

### Download
Download MicroGradient using git:
```shell
git clone 
```

## Usage
MicroGradient could predict trends of microbial genomes.The process involves some steps:

1. Obtain microbiome abundance data.
2. Calculation of correlation coefficients from microbiome abundance data.
3. Data preprocessing to conform data to input format.
4. Predict microbiome trends by MicroGradient.




