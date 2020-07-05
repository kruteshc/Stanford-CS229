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

### Gradient Descent: Batch for Linear Regression

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

The deravitive of the sum is the sum of the derivaties.


For linear regression, it turns out that if j(O) is sum of squared sums then it turns out to be a quadratic function.
j(o) does not have local optima ( the onyl local optima is also the global optima). 

 ![Gradient Descent on Linear Regression](  https://user-images.githubusercontent.com/62080661/86540503-e5bd8080-bed3-11ea-8282-1da93c0f3e73.png )
 
The other way to look at this is by looking at contours of the plots (image above). Looking at the big bowl and taking horizontal slices and plotting the edges of the horizontal slices. Essentially what it will be is a ellipsis ( as seen below )

 ![Gradient Descent on Linear Regression](  https://user-images.githubusercontent.com/62080661/86540486-c6beee80-bed3-11ea-8b89-58af5eda1eff.png)

Direction of steepest descent is always at 90* (orthogonal to the contour direction) As we go down hill, there is only 1 local mimium hence it will eventually converge. 

If the alpha too large, you'll run past the minium.. if too small, it'll take forever. In pratice, we experiement. If the cost function increases then you know that learning rate might be too large. 

With each iteration of gradient descent, it's trying to minimize j(O) (cost function)... minimize 1/2 of the sum of squared errors of the predictions.

If you add multiple times in gradient, you go uphill not downhill. Thats why we subtract the value (learning rate/gradient descent) from theta.

Our gradient descent here calculates the deratives on entire training set (m). So sometimes this version of gradient descent is also known as Batch Gradient Descent.

Disadv. if you have a giant dataset, in order to make 1 update to your parameter (for one iteration), then we have to scan through the entire dataset for m (ex 100M ) then this constricts processing power


An Alternative to batch gradient descent,

### Stochastic Gradient Descent

 ![Sotchastic Gradient Descent]( https://user-images.githubusercontent.com/62080661/86540478-adb63d80-bed3-11ea-859a-9eeb1217cdec.png )


So instead of scanning through all million examples before updating theta, instead in inner loop of the algorithm , take the gradient descent step using just 1 single example (example i)


What this algorithm is essentially doing, we intialize and then go with 1 st house and then adjust j(o) again and then 2nd etc. Takes a random task but on average is headed towards the local minimum. Stochastic gradient descent will never quite converge. Cuz u are always running around looking at differnet houses (ex). but allows you to make much faster progress ( so on large datasets, this would work better)

Stochastic to Batch ? [ Mini-batch graident descet ] where you use 100 examples at a time instead of 1 at a time. In practice, when dataset is large we barely switch to batch cuz of just the slow nature

When do you stop ?

Plot J(O) over time and if it looks like it stopped going down then you can say okay stop. One nice thing about linear regression, it has to no local optimum so you run into these convergence debugging issues less often.

## Normal Equation

For special case of linear regression, it turns out that there is a way to solve for optimal value of the paremters O to just jump in one step to global minimum without need iof iterative algorithm like Gradient descent.

Works only for linear regression !

In this method, we will minimize J by explicitly taking its derivatives with respect to the Oj ’s, and setting them to zero. 










