---
title: "Predicting Diabetic Readmissions with Machine Learning/Deep Learning Models"
date: 2023-05-01
excerpt: "Predict Hospital Readmission for Diabitic Patients with Machine Learning Model and Deep Learning Model in a team of three. <br/><img src='/images/portforlio/diabetic-readmission-prediction/diagram.png' width='90%'>"
location: "University of Pennsylvania"
collection: portfolio
---

_This is a course project for CIS545 Big Data Analytics(Spring 2023) at University of Pennsylvania._

# Data Source and Project Objectives
Our machine learning project utilized the "[Diabetes 130-US hospitals for years 1999-2008](https://archive.ics.uci.edu/dataset/296/diabetes+130-us+hospitals+for+years+1999-2008)" dataset from the UCI Machine Learning repository. The dataset includes 49 ranging from basic information like gender, age, and weight to specific medical details such as prescribed drugs and diagnoses.
- Target variable is 'readmitted', indicating the number of days until a patient's readmission to the hospital.
- Our object is to predict the readmission status of patients using various machine learning and deep learning model, aiming to identify factors that influence readmission and improve the model accuracy.


# Data Preprocessing and Exploratory Data Analysis(EDA)
We started with extensive data preprocessing to handle missing values, normalize different scales of features, and convert categorical variables into a suitable format for modeling.
- Drop some unnecessary columns, like `encounter_id`, and `patient_nbr`, which are more like the identifier rather than features.
- We have a lot of categorical features and some categorical data has more than 700 categories, which is not good to be represented by one-hot encoding or ordinary encoding. Therefore, feature selection and composition are vital.
- We use data augmentation, imputation and feature engineering to enhance the dataset's quality and relevance. 
- Utilized the Seaborn to visualize data distribution and feature importance.

# Modeling and Comparison
Our team implemented several ML and DL models, including Gradient Boosted Decision Trees, AdaBoost, and neural networks.
- Training technique: Utilized the cross-validation to ensure robustness and avoid overfitting. Additionally, we also implemented the Ensemble method to combine predictions from multiple models, amining to boost overall prediction performance. 
- Metrics: Compared different models based on the accuracy, precision, recall, and F1-score. 
- Monitor: The training process is monitor by TensorBoard. 

# Challenges and Solutions
During the project, we encountered several challenges, including imbalanced data, sparse features, and varying feature scales. 
- Imbalanced data/Long-tailed distribution: Utilized the SMOTE for balancing the dataset.
- Sparse feature: Implemented L1/L2 regularization to handle sparity.
- Varying feature scales: Utilized the standardization and normalization to solve the varying feature scaling. 
Dispite these challenges, our models demonstrated significant potential in predicting patient readmission with some features. 

# Results
Our project successfully developed pridictive models and get some results:
- A Gradient Boosted Decision Tree, achieved an accuracy of 85% and an F1-score of 83%, outperforming traditional classification algorithms. 
- The fully connected Neural Network also showed promising results with an accuracy of 82% and an F1-score of 80%. 