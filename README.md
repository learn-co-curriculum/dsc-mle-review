
# MLE Review

## Introduction

In some previous sections, we discussed Maximum Likelihood Estimation (MLE). In this lesson, we will review this statistical concept and begin to set the stage for how logistic regression can also be interpreted from that perspective. This will help set the stage for the lessons and labs throughout today in which you will code a logistic regression classifier from scratch. 

## Objectives

You will be able to:
* Understand and explain the MLE in terms of maximizing likelihood/log likelihood vs. minimizing negative log likelihood

## MLE

Maximum likelihood estimation can often sound, academic, confusing and cryptic when first introduced. It is oftern presented and introduced with complex integrals of statistical distributions that scare away many readers. Hopefully, this hasn't been your experience to date. While the mathematics can become complex quickly, the underlying concepts are actually quite intuitive.

To demonstrate this, let's return to our coin flipping example. Let's say that you flip a coin 100 times and get 55 heads. Maximum likelihood estimation attempts to uncover the probability of this coin landing on heads given our observations. You can also think of this similar to our previous hypothesis testing discussions. Given our observations, what is the chance that the coin was fair and had a .5 chance of landing on heads each time? Or what is the chance that the coin actually had a .75 chance of lands of heads, given what we observed? In the case of the coin flip, the answer to these questions is rather intuitive. If we observe 55 out of 100 coin flips, the chance of a coin landing on heads which maximizes the chance of us observing 55 out of 100 coin flips is .55. In other words, MLE would simply return the current sample mean as the underlying parameter that would make our observation most probable. Slight deviations to this would be almost as probable but slightly less so, and large deviations from our sample mean should be rare. This all should intuitively make some sense; as our sample size increases, we expect the sample mean to converge to the true underlying parameter. MLE takes a flipped perspective, asking what underlying parameter is most probable given our observations.

## Log Likelihood

When calculating maximum likelihood, we often use a the log likelihood, as taking the logarithm can simplify calculations. For example, taking the logarithm of a set of products allows us to decompose the problem from products into sums. (You may recall from high school mathematics that $x^(a+b) = x^a \bullet x^b$. Similarly, taking the logarithm of both sides of a function allows us to transform products into sums. 

## MLE for a Binomial Variable

Let's take a deeper mathematical investigation into the coin flipping example above. 

In general, if we were to observe n flips, we would have observations $y_1, y_2, ..., y_n$.

In maximum likelihood estimation, we are looking to maximize the likelihood:  

$L(p) = L(y_1, y_2, ..., y_n | p) = p^y (1-p)^{n-y}$  where $ y = \sum_{i=1}^{n}y_i$

Taking the log of both sides:  

$ln[L(p)] = ln[p^y (1-p)^{n-y}] = y ln(p)+(n-y)ln(1-p)$

If y = 1,2,...,n-1 the derivative of ln[L(p)] with respect ot p is:

$\frac{d\,ln[L(p)]}{dp} = y (\frac{1}{p})+(n-y)(\frac{-1}{1-p})$  

As we have seen previously, the maximum will then occur when the derivative equals zero:  

$0 = y (\frac{1}{p})+(n-y)(\frac{-1}{1-p})$

Distributing, we have

$0 = \frac{y}{p} - \frac{n-y}{1-p}$

And solving for p: 

$ \frac{n-y}{1-p} = \frac{y}{p} $

$p(n-y) = \frac{y(1-p)}{p}$  
$\frac{n-y}{y} = \frac{1-p}{p}$  
$\frac{n}{y}-1 = \frac{1}{p}-1$  
$\frac{n}{y} = \frac{1}{p} $  
$p = \frac{y}{n}$  

And voila, we have verified the intuitive solution discussed above; the maximum likelihood for a binomial sample is the observed frequency!
 
## Additional Resources

For more review on MLE, take a look back at some of our previous lessons [here](https://github.com/learn-co-curriculum/dsc-2-21-11-PE-MLE).
## Summary

In this lesson we briefly reviewed maximum likelihood estimation. In the upcoming lesson, we will see how logistic regression can also be interpreted from this framework, which will help set the stage for you to code a logistic regression function from scratch using NumPy. Continue on to the next lesson to take a look at how this works for logistic regression.
