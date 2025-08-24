---
layout: post
author: Su Jiesheng
title: "Applied Data Science Project Documentation"
categories: ITD214
---
## Project Background
Mental health issues such as depression, anxiety, and burnout remain prevalent, particularly among younger generation. Despite growing awareness,  stigma around mental illness still persists and generally people still see mental illness as sign of weakness and shun discussions on mental illness.
 Mental health issues often go unnoticed early, only to be identified later when treatment becomes more resource-intensive.
We are a team in MOH Office for Healthcare Transformation (MOHT) that is tasked to look at how we can have early detection of mental illness through a data-centric approach. 

Our Team Business goal is to develop a data-driven solution that identifies early warning signs and key contributing factors of mental health challenges among adults, with the aim of enabling timely intervention and reducing the risk of long-term mental health deterioration.

This project will be focusing on analysing social media posts to detect early signs of mental distress (e.g. anxiety, suicidal).
## Work Accomplished
Below is a brief overview of the work done. Dataset is provided in the link below this page.

<img width="1862" height="368" alt="image" src="https://github.com/user-attachments/assets/b7f2786c-743f-44d6-a511-8a19e6be9ffe" />

### Data Preparation
Data preparation is categorised into 3 different portions.

Data-Cleaning and Transfomation: We remove NA rows and also created a new variable called length of sentence.

Text Pre-Processing: Lowercase text, remove mention/Hashtag, Remove "httP:'/ annotated word, remove punmctuation/numbers and stopwords cleaning

Text Vectors Creation: We made use of Text Vectorisaion by Keras for our RNN(LSTM) Model and TF-IDF.

Since the data is also skewed. We are did a SMOTE on the data to prevent data biasness.

Due to limited processing power,  we sample 5000 data from the our dataset. We split the data up into 80% train and 20% Test data. The 80% Train data is further split in 80% Train and 20% Validation data.

### Modelling

We have explored a few models for sentimental analysis.
We tried a deep learning model RNN(LSTM) due to its longer term memory and better at text analytics. We have added Dropout layer and early stop to prevent overfitting. Optimiser used: "Adam" and Loss function as Sparse_Categorical_CrossEntropy. Input Vector is Text Vectorisation by Keras.

We also did a tradition approach by using TF-IDF for the following models.

1) A Simple 2 hidden layer Neural Network with dropout layer
2) Random Forest (Default Setting)
3) Decision Tree( Default Setting)

Hyper-Parameters were also tried on the Feedforward Neural Network using RandomizedSearchCV.
   

### Evaluation
Models were assessed based on Accuracy and Recall parameters

The Higher the Accuracy , the better the model

The Higher the Recall,the better the model as we want to reduce False Negative. It is bettter to classify false cases as postive and get human intervention for assessment.

Lowest performing model is the RNN(LSTM) Model with accuracy of 0.41 with low recall across all the categories of target variables.

Highest performing model is the 2 hidden layers feedforward network with accuracy of 0.90 with the highest recall values across all categories of target variables

Random Forest and Decision both perform better than RNN(LSTM) but worse than the Neural Network.

Hpyer-paramater tuning was thus performed for the best performing model the Feedforward Neural Network with RandomizedSearchCV but accuracy did not perform better after tuning probably with iterations too little.

## Recommendation and Analysis

Further hyperparameter fine-tuning can be done using Gridsearchcv which perform an exhaustive search or try RandomizedSearchCV with more iterations

LSTM originally was thought to be the better model but with sample of only 5000 out of the 50000 data, it was unable to perform as data is too little to train LSTM before result in overfitting. Even the neural network model start to overfit at Epoch 6.

More processing power is needed to process more data and deep neural network such as LSTM would definitely perform better because we are able only to performing machine learning with 10% of the dataset

Conclusion: With the simple 2 hidden layer neural network, we could crawl the social media post and possibly detect potential mental-ill patients with an accuracy of 0.9.

## AI Ethics
Due to the dataset being predominantly gotten online social media posts, the demographics are skewed towards younnger generations/tech-savy groups. This could cause biasness and representation.

As our final models are using deep-learning models, it could be a black-box for most users and this could limit our visibilites on how certain predictions are made. We could use SHAP or LIME to help interpret predictions and show which words have a heavier weight in the model.

We must certainly be using Human-in-the-loop Validation as feedback loop for these high risk predictions as any wrong predictions even if its just 1 person could lead to detrimental effects on the person life


## Source Codes and Datasets
The link to the python code and dataset is https://github.com/Elftain/itd214_proj. 
