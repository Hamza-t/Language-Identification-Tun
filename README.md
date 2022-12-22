# Language-Identification-Tun : a project to predict the langage of text (arabic/english/french/tunizi/code-switching)


## General Introduction : What is language identification in NLP?

In natural language processing, language identification or language guessing is the problem of determining which natural language given content is in. Computational approaches to this problem view it as a special case of text categorization, solved with various statistical methods.

---

## Project Workflow

We will be using the following workflow:

![workflow](https://user-images.githubusercontent.com/71349228/209234269-9e77e0d9-a8c6-4a4f-9f04-050449f770b2.png)

## 1. Data collection
![data_collection](https://user-images.githubusercontent.com/71349228/209234599-4b8ab710-582c-4bb9-ab2c-74848e51dce8.png)

### a. Scrape Comments from Youtube
This task is done in the python environment of my desktop with selenium and webdriver. 

### b. Collecting Public Dataset
We have 2 different datasets :
1.  TUNIZI: (dataset in Tunisian Arabizi) https://github.com/chaymafourati/TUNIZI-Sentiment-Analysis-Tunisian-Arabizi-Dataset
2.  TSAC: (mix of Arabic, French, and Arabizi) https://github.com/fbougares/TSAC

### c. Annotation
this task have completed in the class

Attribute to each sentence, a label, from these 5 classes:

* Arabic: all the letters/words are in Arabic
* French: all the letters/words are in French
* English: all the letters/words are in English
* Tunizi: words are written in the Tunisian Arabizi (Latin chars with numerics)
* Code-switching: the sentence is a mix between more than 2 languages.


## 2. Data preparation
![data_preparation](https://user-images.githubusercontent.com/71349228/209235029-0e68eea7-e2f6-4827-a366-cbf49e8afb60.png)
* we will merge all data file in one data frame and insure the type of each column
* The final data will contain just 2 columns : "text" and "label"
* The "text" column shoold be string, the "label" column shoold be integer

## 3. Data cleaning
![data_cleaning](https://user-images.githubusercontent.com/71349228/209235388-e5ff0c91-d0bb-4a9d-9f66-fc0d96d7e85f.png)

In this step, we will clean text in our data file

1. Delete duplicate rows and Nan values in labels column.
2. Change the type of data (text column must be string and label colmn must be integer
3. Clean text data from : URL, emojis, punctuation (?,:!..) , symbols, newlines and Tabs. : Example : To know more about this website: https://Hamza.example.com
4. Remove Accented Characters. : é, à, ...
5. Reduce repeated characters. : eyyyyyy (mean "yes") ==> ey
6. Remove Whitespaces : "How are you doing ?" Case Conversion : str.lower()

## 4. Data visualization
With writing some python code, we can see some beautiful informations about our data
![graph1](https://user-images.githubusercontent.com/71349228/209235769-28c68729-b38f-46eb-9bcc-196c09402fbb.png)
![graph2](https://user-images.githubusercontent.com/71349228/209235835-a6796808-5274-4b38-b99b-c95691ad87b8.png)
![graph3](https://user-images.githubusercontent.com/71349228/209235875-e9094b33-0249-4d45-9e5d-191fb4358a95.png)
![graph4](https://user-images.githubusercontent.com/71349228/209235885-978f9cc1-91fc-4317-a5bd-f8a8bf7b04d1.png)



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

