---
layout: post
title: Why functional programming?
description: "functional programming for the simple minds"
tags: [ code]
comments: true
---

Last week I got the opportunity to attend a talk on functional programming using Clojure at thoughtworks Uganda geeknight(trying to look to link but I can't find it). I found this talk interesting with the presenter making brilliant use of functional thinking and decided to do a deep dive into functional programming. I started off by reading [Why functional programming matters by John Hughes](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0CB0QFjAA&url=http%3A%2F%2Fwww.cse.chalmers.se%2F~rjmh%2FPapers%2Fwhyfp.pdf&ei=BEZVVOPgFMOrPKW4gYgI&usg=AFQjCNGSJfyki6IWtpJeTA1-kWszquHyew&sig2=pXEKtm9O_fdnB27_ZQatDA) and then reading the blog [Functional Programming For The Rest of Us](http://www.defmacro.org/ramblings/fp.html).

#Functional thinking in python
Well i'm not conversant with Clojure , I've used a bit of scala however that doesn't mean I can't reap the advantages of fucntional programming in other languages.So functional programming is a set of ideas.Functional programming is primarly deals with calculations and uses functions to perform them. Functional programming allows us to keep the state of using functions and not variables. The state is usually kept in the function parameters. An example of doing this in our everyday function is using recursion. See python example below to reverse a string.
{% highlight python linenos %}
def reverse(n):
    if len(n)<2 :return n
    return reverse(n[:1])+n[0]
{% endhighlight %}

The function above is functional style. however its a memory hog as it keeps repeatedly assigning itself objects. So why would some want to use this?

#Benefits of Functional programming

##Unit testing

Functional programs have no side effects that is to say no external function or forces can change variables in a function. That means when testing all one has to worry about is the arguements passed to the function and the value returned

##Debugging

Functional programs depend only what's passed through the arguments. So when there's a bug reproducing is easy since you look through the stack its the arguments passed to the function and its return values compared to imperative programming where external states can modify variables.

##Concurrency
With functional programs  one doesn't have to worry about race conditions or deadlocks. No functional data is accessed by more than one thread or the same thread twice. Turns out Ecrission designed a functional language Erlang to help deal with concurrency issues for use in telecommunication switches.

This article only scratches the surface of functional programming. Well a small scratch can grow into a bigger scratch