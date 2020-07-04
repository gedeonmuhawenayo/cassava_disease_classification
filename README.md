# Cassava Disease Classification

> Classify cassava plants as belonging to one of 4 various disease classes or healthy

![Cassava Diseases](cassava11-19-07.png "Cassava Diseases")

## Overview

Computer vision models has been proven to perform well with large amount of training data. They are also useful for transfer learning to similar domains as the original training data. Can we apply these models to help predict disease class for cassava plants?

The disease classes include;

- Cassava Mosaic Disease
- Cassava Brown Streak Disease
- Cassava Bacterial Blight
- Cassava Green Mite

This repo contains various things we tried during the project. A report on our findings can be found in the  `Report on Cassava Disease Classification.pdf`

## Getting Started

The `cassava_disease_classification.ipynb` notebook contains all the codes required to explore and run our models.

To learn more about the original competition, I attached a pdf file named `CassavaDisease.pdf` with  highlighted texts that shows the main points in the paper.

The competition contained extra-data which can be utilized for better predictions. We used the pseudo-labelling method to deal with the extra data.

I wrote an article during this project to explain how to easily perform k-fold cross validation with image data. Also, since the number of examples for the classes were not balanced, we adopted the Stratified-Kfold sampling to ensure easy class is represented in the sampling.

The article can be found here; [Cross Validation and Reproducibility in Neural Network Training](https://ogunlao.github.io/2020/05/08/cross-validation-and-reproducibility-in-neural-networks.html)

Also, I wrote a [Kaggle kernel](https://www.kaggle.com/ogunlao/crossvalidation-for-cassava-disease-classification) to explain cross validation. It can easily be modified to also make predictions.


## Lessons Learnt

- Cross validation is important especially for small datasets 
- Ensemble of models and Test Time Augmentation(TTA) are tools for making more accurate predictions. In all our models, predictions using TTA during prediction had better accuracy.
- Larger models such as ResNet101 cn easily overfit, so they should be regularized using methods like dropout.

## License
[MIT](https://choosealicense.com/licenses/mit/)