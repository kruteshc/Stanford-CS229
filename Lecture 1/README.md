# Intro to CS229: Machine Learning

" AI is the new electricity... Applications of ML vast any specefic industry "

Pre-Requisite: 
1. Basic computer knowledge like binary tress & probability ( random variable, expected value, variance )
2. Basic Linear Algebra: Matrics, Eigen Vectors, etc. 
Class is highly technical with goal to uncover the hood under various algorithms.

## What is Machine Learning ?

A field of study that gives computers the ability to learn without explicitly programmed.

A computer program is said to learn from experience E with respect to soem task T and some performance measure P, if its performance of T, as measured by P, improves with experience R

## Supervised Learning: 

In supervised learning, you are given a dataset (x,y) and your goal is to learn the mapping from x to y. To describe the supervised learning problem slightly more formally, our goal is, given a training set, to learn a function h : X 7→ Y so that h(x) is a “good” predictor for the corresponding value of y. For historical reasons, this
function h is called a hypothesis

Ex. Given data, how can we learn to predict the prices of other houses in poertland, as a function of the size of their living areas ? 

The above problem is a regression problem as value Y we are trying to predict is continous 

Ex. Breast tumors and trying to decide with a tumor is belign or malignant ?

The above problem is a classification problem as y (target variable) in this case can only take on discrete values. 


Most of the ML algorithm, often be giving multiple features to predict another number. For ex, instead of only tumor size.. we can have multiple features such as age of patient & tumor size and asked to predict Y (cancer or no cancer)
In practice, we have a lot more features such as clump thickness, uniformity of cell size/shape, adhesion, etc.

Well in case of so many input variables, we will learn about SVM that uses infinite input variables/features. well we can't store this many variables in computer storage, we will learn how to use a technical method called kernels that work well with infinitely long list of features.

## Machine Learning Strategy ( Learning Theory )

Andrew Ng.: there is a huge difference in effectiveness of how 2 different teams can apply the same learning algorithms.  Most skilled DS practionoer is very strategic. Skill at deciding architecture choices are crucial. 

Help you become more systematic as a more systematic engineering discipline. When you run a learning algo, it almost never works on first try. Debugging is quite crucial.

Working on evolving from black magic to more systematic approaches.

## Deep Learning

ML's subset that is advancing quite rapidly so you can understand basic of how to train neural networks. 

## Unsupervised Learning: 

Discover strucutre in data without defined out Y(target variable) / unlabelled data.

Ex. if you have multiple microphones in a room of lots of people talking, how can you separate out voices of differnet peoples voices ?

Most of the recent wave of economic value has been with supervised learning but there are very exicting problems we can cover unsupervised learning

## Reinforcement Learning

Imagine there is a stuck helicopter, can you write a program to make it fly. We can use reinforcement learning to use this.

What is it ? 

Think of it like training a dog, so you let the dog whatever it wants and when he does good things we say GOOD BOY & vice versa BAD BOY. Figure out what actions to control over time for desired results

By giving reward signals, we can have learning algorithm learn itself how to optimize the reward. Most recent applciations has been atari games etc. 






