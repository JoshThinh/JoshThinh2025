---
layout: post
title: MCQ Review
description: College Board Test 2015 Practice Exam MCQ Review
categories: ['Collegeboard']
permalink: /collegeboard/mcq
type: collab
comments: True
---

## MCQ Reflection
I struggled the most with arrays and 2D arrays in the 2015 CSA multiple-choice questions, so I know I need to focus on improving in this area.

To get better, I’ll start by reviewing the basics of arrays: how they’re declared, initialized, and accessed. I often mix up the indexing, so I plan to practice with smaller examples to strengthen my understanding.

I also want to work on how I loop through arrays, especially 2D arrays. I’ll focus on correctly handling the row and column indexing and practice basic operations like summing elements or searching for values.

Instead of jumping into complex problems, I’ll break them down into simpler parts. I’ll solve smaller problems first and build up to the bigger ones.

By practicing more and reviewing my mistakes, I’m confident I can improve my understanding of arrays and 2D arrays.

## MCQ Review
Here is the Review of the 2015 Practice Exam MCQ [test link](https://apclassroom.collegeboard.org/8/assessments/results/63893231/performance/537990)

### Array
- Q4 findMax of 1D int array
![test]({{ site.baseurl }}/images/notebooks/foundation/4r.png)
![test]({{ site.baseurl }}/images/notebooks/foundation/4gs.png)
If you got the question wrong, you might have thought findMax wouldn’t work if all values were negative. However, that’s not true if the method is correctly implemented. The key is to initialize the maximum as the first element of the array, not 0 or any other fixed value, and properly compare each element. The method should handle negative numbers just fine as long as these conditions are met.
- Q13 mystery method with pairwise traversal of array
![test]({{ site.baseurl }}/images/notebooks/foundation/13r.png)
![test]({{ site.baseurl }}/images/notebooks/foundation/13gs.png)
If you got this question wrong, you might have misunderstood what mystery(3) does. The mistake could be assuming it shifts or sorts values instead of modifying them based on a pattern.
The key correction is to focus on how each element is changed. Most likely, mystery(3) adds or modifies values by a pattern involving 3 (like adding 3 to every third element or using a mathematical operation). Understanding the exact pattern will help you predict the correct order of values.
- Q33 Find maximum in 1D int array
![test]({{ site.baseurl }}/images/notebooks/foundation/33r.png)
![test]({{ site.baseurl }}/images/notebooks/foundation/33gs.png)
If you got this question wrong, you might have misunderstood how each segment handles the initialization of max.
The key correction is to recognize that:
I works because it starts with the smallest possible integer, ensuring it can handle all values in arr.
II works by setting max to the first element on the first pass, handling negative values correctly.
III works by directly starting max as the first element.
All three handle negative values and different array contents properly, so the correct answer is indeed I, II, and III.
- Q37 concatWords method with String array
![test]({{ site.baseurl }}/images/notebooks/foundation/37r.png)
![test]({{ site.baseurl }}/images/notebooks/foundation/37gs.png)

### 2D Array
- Q8 operation method on 2D int array
![test]({{ site.baseurl }}/images/notebooks/foundation/8r.png)
![test]({{ site.baseurl }}/images/notebooks/foundation/8gs.png)
- Q31 X and O board
![test]({{ site.baseurl }}/images/notebooks/foundation/31r.png)
![test]({{ site.baseurl }}/images/notebooks/foundation/31gs.png)
### Primitive Types
- Q18 Print statement with mathematical operators
![test]({{ site.baseurl }}/images/notebooks/foundation/18r.png)
![test]({{ site.baseurl }}/images/notebooks/foundation/18gs.png)
### Iteration
- Q1 numDivisors of given int inputVal
![test]({{ site.baseurl }}/images/notebooks/foundation/1r.png)
![test]({{ site.baseurl }}/images/notebooks/foundation/1gs.png)
### Recursion
- Q38 mystery method with 1D int array, v and numVals
![test]({{ site.baseurl }}/images/notebooks/foundation/38r.png)
![test]({{ site.baseurl }}/images/notebooks/foundation/38gs.png)

### ArrayList
- Q34 listOfWords List and wordsWithCommas method
![test]({{ site.baseurl }}/images/notebooks/foundation/34r.png)
![test]({{ site.baseurl }}/images/notebooks/foundation/34gs.png)


