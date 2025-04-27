# Kaggle-ის კონკურსის მოკლე მიმოხილვა

ამ პროექტში დავამუშავე IEEE-CIS-ის ფraud detection dataset, სადაც ამოცანა იყო ტრანზაქციების თაღლითობის (fraud) პროგნოზირება.

# ჩემი მიდგომა პრობლემის გადასაჭრელად

მონაცემების წინასწარი გაწმენდა და ოპტიმიზაცია (memory optimization)

Feature Engineering (ახალი ფუქციების გენერირება)

Feature Selection (არასაჭირო ფუნქციების მოცილება)

სხვადასხვა მოდელების ტრეინინგი (XGBoost, RandomForest, Logistic Regression, LightGBM)

Hyperparameter ტესტირება

საბოლოო შედეგების შეფასება Validation AUC-ით

MLflow-ის გამოყენებით ექსპერიმენტების ლოგირება


## რეპოზიტორიის სტრუქტურა

model_experiment_XGBoost.ipynb — XGBoost-ის ექსპერიმენტები

model_experiment_RandomForest.ipynb — RandomForest-ის ექსპერიმენტები

model_experiment_LogisticRegression.ipynb — Logistic Regression-ის ექსპერიმენტები

model_experiment_LightGBM.ipynb — LightGBM-ის ექსპერიმენტები

model_inference.ipynb — საუკეთესო მოდელის გამოყენებით პროგნოზირება და submission ფაილის გენერირება

README.md — პროექტის აღწერა


## Feature Engineering

TransactionAmt-ის group mean ratio

Email domain match

Frequency Encoding (card1, card2, addr1 და სხვა ცვლადებზე)

## NaN მნიშვნელობების დამუშავება

რიცხვითი ცვლადებზე median იმპიუტაცია

კატეგორიულ ცვლადებზე constant ("missing") იმპუტაცია



# Feature Selection

არასაინტერესო V-ფუნქციების ხელით მოცილება

მხოლოდ საჭირო ფუნქციების დატოვება (EDA-ის საფუძველზე)

# Training

Cross-validation 5 folds

Balanced classes

Model averaging (k models)

## ტესტირებული მოდელები

XGBoost

RandomForest

Logistic Regression

LightGBM

## Hyperparameter ოპტიმიზაციის მიდგომა

XGBoost: max_depth, learning_rate, colsample_bytree

RandomForest: n_estimators, max_depth

Logistic Regression: penalty, solver

LightGBM: boosting_type, learning_rate, num_leaves

## საბოლოო მოდელის შერჩევის დასაბუთება

Validation AUC-ის მიხედვით საუკეთესო შედეგი აჩვენა XGBoost მოდელმა.

## MLflow Tracking

ყველა preprocessing, feature engineering, feature selection, training ლოგირებულია ცალკე run-ებად.

თითოეული მოდელის ექსპერიმენტი გამოყოფილია (მაგალითად, XGBoost_Training, RandomForest_Training და ა.შ.)

# MLflow ექსპერიმენტების ბმული

https://dagshub.com/lkata22/IEEE-CIS-Fraud-Detection.mlflow/#/experiments/0?searchFilter=&orderByKey=attributes.start_time&orderByAsc=false&startTime=ALL&lifecycleFilter=Active&modelVersionFilter=All+Runs&datasetsFilter=W10%3D

# საუკეთესო მოდელის შედეგები (ვალიდაციაზე)

XGBoost	- 0.96091

RandomForest - 0.86915

Logistic Regression	- 0.65577

LightGBM - 0.95622
