# Lecture 2

#### Outline for Today:

    1. Linear Regression
    2. Batch.Sotchastic Gradient Descent
    3. Normal Equation

## Linear Regression: 

One of the simplest learning algorithms. 

#### Ex. Lets say you want to predict prices of houses (Y) based on house size (x1).

To perform supervised learning, we must decide how we're going to represent functions/hypothesis h in a computer.

The process of supervised learning is that you have a training set that you fit through the learning algorithm and its job is to output a function to make predictions of y ( this outpout can be called an hypothesis). So we can input a size of diff house (x) & will output the estimated price (y).

The way you go above structuring a ML problem is key. these are key decisions we have to make any ML Design.

The first thing we need to ask:
1. How to represent the hypothesis (H).

We are going to say the hypothesis for ex is going to be H(x) = O + O1(X) / Y = mx + b. If we have more variable, so H(x) = O + O1(X1) + O2(X2) where X1 is size of the house and X2 is # of bedrooms.
   
In order to make that notation simpler, 
   
![Linear Regression Representation](https://user-images.githubusercontent.com/62080661/86197748-0d06fd00-bb24-11ea-82fd-bfbaab1d040c.png)
   
where X0 = 1 where O = [ O1, O2, O3 ] amd features become X = [X0, X1, X2] where X0 = 1 and X1 = size of house X2 is # of bedrooms
   
So O (theta)  is parameters annd job of learning algo is to choose proper O to allow you to make predictions ( Think of O as essential M / slope)
   
           O(theta) = parameters
           m = # of training examples [ # of rows in ex. ]
           n = # of features
           x = input variable/ Features
           y = target variable / Output
           (x,y) = Training example
           (xi,yi) = ith training example

2. How do you choose parameters (theta) ?

What we will do is we will choose theta such that H(x) ~ Y for the training examples. H depends both of X (input features) & Y. 
Htheta(X) = H(X) just for simplicity but keep in mind H depends on both X & Y.
  
##### Ordinary Least Square 
Essentially, we will want to minimize squared difference between what the hypothesis outputs (prediction) & Y (correct price. 
  
![Ordinary Least Square](https://user-images.githubusercontent.com/62080661/86198340-6cb1d800-bb25-11ea-9e1b-54acccbc0e31.png)

Why squared error ? Generalized linear models.. linear regression is just part of a bigger family. Justification will come in a lecture or 2.

Let's see how we can implement an algorithm that can minimize the cost function (J of O (theta)

### Gradient Descent

We are going to start with some value of O (theta), which starts with some intital O, and repeatedly performs update O (theta) to reduce J(O)/cost function.

![Gradient Descent](https://user-images.githubusercontent.com/62080661/86198875-9ae3e780-bb26-11ea-8323-36a0befe3601.png)

Find values for O0 & 01 that minimize the height of the surface J(O). In gradient descent, you start off at some point on the surface by intializing O0 or O1 rnadomly. Imagine you are standing at a point in hill, what we do is turn around 360 degress and see if you were to take a tiny little step, in what direction should you take it ? with goal of trying to go downhill as fast as possible.
( go to lowest possible point in the surface)/ Steepest gradeient downhill.  (lowest possible point is essentially a local optima)

You can start at any step. So imagine you were standing somewhere else then your path would be different and you would have gotten to the different local optima.

Oj gets updated as:

![Gradient Descent](https://user-images.githubusercontent.com/62080661/86199215-83f1c500-bb27-11ea-90cd-18a6027cf202.png)

So in each separate gradient descent, for each value of J, update it according O(J) - Learning Rate (Partial derative of cost function J(O) with respect to paramter Oj)
Well so the partial derative calculation is, ( derative of function defines the direction of steepest descent)

![Partial Derative: Gradient Descent](https://user-images.githubusercontent.com/62080661/86199355-eb0f7980-bb27-11ea-9f7a-3a896041fd61.png)

 So one single training example, gives us: 
 
 ![Single training example]( https://user-images.githubusercontent.com/62080661/86199871-3ece9280-bb29-11ea-8415-43decb60fcfa.png)
 
 The goal here is to repeat until convergence. Each iteration of gradient descent, you do this update for J = 0,1,n where n is number of features.
 
 ![Goal](  https://user-images.githubusercontent.com/62080661/86200011-9d940c00-bb29-11ea-8537-e15b1c8d007a.png )


# PAUSED AT 33:40
