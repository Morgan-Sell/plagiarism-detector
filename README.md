# Detecting Student Plagiarism

![Graded Paper](https://github.com/Morgan-Sell/plagiarism-detector/blob/master/images/grading_main.jpg)

## Executive Summary

This project is comprised of 95 student submissions and five original sources. The topic of each student paper corresponds to one of the original sources' subject matter. The objective of the model designed for this project is to detect whether a student's paper is plagiarized. The extent of plagiarism ranges from cut (and pasted), heavey, light and not (plagiarized). "Lightly" copied presents the most challenging case in detecting plagiarism.

The source document subjects include OOP, PageRank, vector space model, Bayes' theorem, and dynamic programming.

The graph below summarizes the the dataset's distribution of the degree of plagiarism.

![Degree Plagiarism Plot](https://github.com/Morgan-Sell/plagiarism-detector/blob/master/images/plagiarism_distribution.png)

By applying NLP, the Adapative Boosting (AdaBoost) model achieved an accuracy equal to 0.92. 

## Data Processing and Feature Engineering

To prepare the data, all words were located and all non-alphanumerical and tabs/additional spacing were removed.

Set theory was used to calculate the containment(see equation below). This feature evaluates the degree in which the selected ngram is duplicated in the student's submission. The metric is normalized enabling comparison among documents that vary in length.

>$$ \frac{\sum{count(\text{ngram}_{A}) \cap count(\text{ngram}_{S})}}{\sum{count(\text{ngram}_{A})}} $$

Containment was calcuated using ngram values ranging from one to six. 1-gram and 6-grams were selected because the other n-grams shared a high correlation among each other. Highly correlated features may overinflate the importance of a single feature.

Dynamic programming was used to derive the lowest common subsequence (LCS). The LCS is longest string of words shared between two documents. Dynamic programming searches the document from left to right. The subsequences' orders must be consistant; however, the words are **not** required to be in the same indices/locations throughout the two text documents. This metric is normalized by by the total number of words in the student's submission.

## Model Design and Evaluation

As previously mentioned, the _lightly_ plagiarized documents present a challenge. Consequently, a model that learns from its prior would be best suited for this problem. Therefore, AdaBoost was applied.

One major downsize of AdaBoost is that it's computationally expensive. For this project that weakness is marginalized because of the small dataset.

The model achieved an accuracy score equal to **0.92**. Below is the resulting confusion matrix.

![Confusion Matrix](https://github.com/Morgan-Sell/plagiarism-detector/blob/master/images/cf_matrix.png)


## Notes / Sources
This project was completed as part of Udacity's Machine Learning Engineer Nanodegree program. This data is a slightly modified version of a dataset created by Paul Clough and Mark Stevenson at the University of Sheffield

## Required Packages
- numpy
- pandas
- sklearn
- matplotlib
- seaborn
- os
- boto3
- sagemaker
- re