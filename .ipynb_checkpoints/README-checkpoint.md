# Detecting Student Plagiarism

[Graded Paper](https://github.com/Morgan-Sell/plagiarism-detector/images/students_grade.jpg)

## Executive Summary

This project is comprised of 95 student submissions and five original sources. The topic of each student paper, e.g. OOP, corresponds to one of the the topics in the original sources. The objective of the model designed for this project is to detect whether a student's paper is plagiarized. The extent of plagiarism ranges from original (not plagiarized), heavy, lightly, and completely copied. "Lightly" copied presents the most challenging case in detecting plagiarism.

The graph below summarizes the the distribution of degree of plagiarm for the dataset.

[Degree Plagiarism Plot](https://github.com/Morgan-Sell/plagiarism-detector/images/plagiarism_distribution.png)

By applying NLP, I 

## Data Processing and Feature Engineering

To prepare the data, I lowercased all words and removed all non-alphanumerical and tabs/additional spacing.

I applied set theory to calculate the containment(see equation below). I selec

$$ \frac{\sum{count(\text{ngram}_{A}) \cap count(\text{ngram}_{S})}}{\sum{count(\text{ngram}_{A})}} $$