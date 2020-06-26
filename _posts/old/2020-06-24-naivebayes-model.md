---
layout: post
title: Naive Bayes Python Implementation
image: /img/bayes_cover.png
comments: false
---

<h1>Overview</h1>

## [Naive Bayes Classifier](https://en.wikipedia.org/wiki/Naive_Bayes_classifier)

Bayes’ Theorem is a way that we can calculate the probability of a piece of data belonging to a given class, given our prior knowledge.

Bayes’ Theorem is stated as:

    P(class|data) = (P(data|class) * P(class)) / P(data)

Where P(class|data) is the probability of class given the provided data.

Naive Bayes is a classification algorithm for binary (two-class) and multi-class classification problems.
It is called Naive Bayes because the calculations of the probabilities for each class are simplified to make their calculations tractable.

while calculating the class probabilities the naive bayes algorithm will assume that the features are statistically independent of each other. this assumption is rather strong compared to real world data, however this approve works surprisingly well even on data that doesn't have independent features.

During the calculation of probabilities it should be noted that I’m using a CI of 0.95 and that any value that hit’s that borderline is rounded down unless there is not another prediction that meets that minimum threshold then the label with the highest percent chance of occurring for the particular prediction is used.

For the case that there are headers in the dataset then the headers are dropped because they have little use for testing the algorithm’s effectiveness.

The training data set is going to be the iris dataset from uci machine learning repo. This dataset was picked because it’s popular and it has mostly numeric features, during the process of development I had some problems dealing with any categorical features without using sklearn libraries to impute and encode them so I opted with the safe route and went with the iris set.

In addition to the ease of use the iris set was also used because it showcase the instance of features that are correlated being used with the naïve bayes algorithm, which as stated above goes against the natural assumptions of the NB algorithm.

The tests are compared to the sklearn NaiveBayesClassifier, during the testing I noticed that the runtime of my implementation is terrible compared to the sklearn implementation.
This fact doesn’t surprise me any because I wrote mine in vanilla python with scipy, numpy, and pandas. Not hardly comparable with the years of development and dedicated C libraries of sklearn.

To improve the runtime of my implementation I could rewrite the code to use less loops and computationally inefficient practices algo with compile the python into C using cython or something similar to make the translation, there are also some specialized libraries in java(mostly Atomic locking and ThreadFactory’s) that would have be useful to break up the algo’s computation at execution time.

For the time that I had and the stumbles that I made this Implementation is the best that I’ve found, that also works as expected with the iris dataset and a generated gaussian set(Not shown but was part of the testing process).

for my full code please see my [Github Repository](https://github.com/Jwilson1172/NaiveBayes) holding all of the source code.
