---
layout: post
title: Tape Equilibrium ,Codility 
description: "Solution Tape Equilibrium"
tags: [ code, highlighting]
comments: true
---

[Syntax highlighting](http://en.wikipedia.org/wiki/Syntax_highlighting) 
I'm back to playing to playing around with codility to help improve on the code write. So I took the Tape Equilibrum test , below is my first submission. On submission , the results were not great. I had a time complexity of O(N*N). This was due to line 8 where I kept calculating the sum of the entire array at each iteration the loop. Also my naming of variables is terrible.
{% highlight python linenos %}
#Tape Equilibrium , first solution
def solution(A):
	Sum1=0
	Output=0
	for i in range(0,len(A)):
		Sum1+=A[i]
		
		Difference=abs(Sum1-(sum(A)-Sum1))
		
		if(i==0):
			Output=Difference
		if (Difference<Output):
	return Output
print solution(A=[3,1,2,4,3])
{% endhighlight %}

Here's a revised solution with much naming of variables and also taking out the unnecassry iteration.
{% highlight python linenos %}
#Tape Equilibrium , revised solution
def solution(A):
  head=A[0]
  tail=sum(A[1:])
  min_dif=abs(head-tail)

  for i in range(1,len(A)-1):
    head+=A[i]
    tail-=A[i]

    if abs(head-tail) <min_dif:
      min_dif=abs(head-tail)
  return min_diff
print solution(A=[3,1,2,4,3])
{% endhighlight %}


