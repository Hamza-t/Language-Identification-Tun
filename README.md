# Language-Identification-Tun : a project to predict the langage of text (arabic/english/french/tunizi/code-switching)


## General Introduction : What is language identification in NLP?

In natural language processing, language identification or language guessing is the problem of determining which natural language given content is in. Computational approaches to this problem view it as a special case of text categorization, solved with various statistical methods.

---

## Project Workflow

We will be using the following workflow:

![workflow](https://user-images.githubusercontent.com/71349228/209234269-9e77e0d9-a8c6-4a4f-9f04-050449f770b2.png)

## 1. Data collection

We have 2 different datasets :
1.  Public Data from kaggle : https://www.kaggle.com/datasets/aditiharsh/mental-health-dataset
2.  Data collected from a survey via social media

We will start by **preparing and cleaning** each dataset than merge them together. 

Then we will encode the resulting dataset.

Finnaly, we will **analyze** the weights of the features in the dataset through a HeatMap in order to select the features we will be using in our first Model.

We will thus obtain two files : ``data_for_model1.csv`` and ``data_for_model2.csv``

## 2. Build, run and evaluate the first Model

After importing the file created previously, we will **scale and split** our dataset into train and test data with 80/20.

Then, we will build 6 different supervised ML models (Logistic Regression, Support Vector Machines, Decision Trees, Random Forest, Naive Bayes and K-Nearest Neighbors).

We will evaluate them by their **recall** because we want to correctly classify if a user may have a mental health issue.

We ended up choosing Naive Bayes Model with ``0.923`` recall.

We will also build a DL model with 3 hidden layers. The model has ``0.92`` f1-score.

We decided to go with the Naive Bayes because we discovered that the DL Model is overfitting.


## 3. Build, run and evaluate the second Model

We will do the same steps as for the first model.

Here we decided to use the Random Forest Model with  ``0.928`` recall.

We will also build a DL model with 3 hidden layers. The model has ``0.9289`` f1-score.

## 4. Conclusion

We will be using the Naive Bayes Model as the first Model then we will be using the Random Forest Model as our second model.

![results](https://raw.githubusercontent.com/ShathaCodes/tuni-hack/main/results.png)

