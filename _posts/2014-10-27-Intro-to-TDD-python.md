---
layout: post
title: Introduction to TDD python
description: "Introduction to TDD python"
tags: [ code]
comments: true
---
I'm currently running our second cohort for our Women in Passion programme and I would like to introduce TDD to my students in a painless way. I believe TDD allows developers to think through their problem before writing the actual solution. In this way, a developer will be forced to think of the design of her solution and the different possible routes. I tend to fall in the trap alot of writing no tests and coming up with a solution that solves the problem in one way and yet there's different possible routes(which takes us to the topic of [test coverage](http://www.thoughtworks.com/insights/blog/are-test-coverage-metrics-overrated)) 

##For starters syntax for Unit Testing

The main methods that we make use of in unit testing for Python are:

* assert - base assert allowing you to write your own assertions
* assertEqual(a, b) - check a and b are equal
* assertNotEqual(a, b) - check a and b are not equal
* assertIn(a, b) - check that a is in the item b
* assertNotIn(a, b) - check that a is not in the item b
* assertFalse(a) - check that the value of a is False
* assertTrue(a) - check the value of a is True
* assertIsInstance(a, TYPE) - check that a is of type "TYPE"
* assertRaises(ERROR, a, args) - check that when a is called with args that it raises ERROR

##Next pip install nose which is a python unit testing package

##Next code

{% highlight python linenos %}
#calculator.py
class Calculator(object):
 
    def add(self, x, y):
        pass
{% endhighlight %}

Here's a revised solution that solves all cases
{% highlight python linenos %}
#testCalculator.py
import unittest
from calculator import Calculator
 
class TddInPythonExample(unittest.TestCase):
 
    def test_calculator_add_method_returns_correct_result(self):
        calc = Calculator()
        result = calc.add(2,2)
        self.assertEqual(4, result)
if __name__ == '__main__':
    unittest.main()
{% endhighlight %}

Writing tests in python is pretty simple
In testCalculator.py,
-import the unittest module from python library
-we add a class to hold all out test cases
-the test method needs to to begin with "test_" which can be picked up nosetest runner for execution


#to be continued

