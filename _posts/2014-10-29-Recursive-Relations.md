---
layout: post
title: Simple Asymptotic Analysis of Recursive Relations
description: "Simple Asymptotic Analysis of Recursive Relations"
tags: [ code]
comments: true
---
Asymptotic analysis is one of those topics that makes my head spin especially when it comes to performing it on recursive functions(recursion already makes my spin so double spin). I think found an easy of determing the run time of recursive functions , hopefully you find it useful.

Lets start with the three laws of recursion.
* A recursive algorithm must have a base case
* A recursive algorithm must change its state and move towards the base case
* A recursive algorithm must call  itself , recursively!!

Given these laws we can come up with a recursive relation to describe the running time of a recursive relation.

                T(n)= a * T(g(n))+ f(n)

where a represents the number of recursive calls , g(n) is the size of each subproblem to be solved recursively and f(n) is any extra work done in the function.

Now lets take this try estimate the runtime for algorithm that finds the nth element in the Fibonacci sequence . 

Below is a code representing the mentioned algorithm:
{% highlight python linenos %}
def fib(n):
    if n<2 :return n
    return fib(n-1)+fib(n-2)
{% endhighlight %}

In the algorithm above we have g(n)s are n-2 and n-1 , a is 2 because we have two g(n)s and f(n) is 1 because we have to perform addition at the end. On our first recursive call we get:

                        T(n)=2T(n-1)+1

On our second recursive call we get:

                        T(n)=2*2T(n-2)+2

On our second recursive ,we have now have 4 recursive calls produced from our two previous recursive calls.
We can see two equations and from our two equations we can come up with similarlities that gives us this :

                         T(n)=2^2T(n-2)+2

Going back to our laws , our base case is always O(1) resulting in T(1)=1 which means n-k=1 or k=n-1. Which means we have :

                             T(n)=2^k T(n-k)+k


We have proved that this algorithm is exponential in a few steps. Go ahead and determine the runtime of other equations!!