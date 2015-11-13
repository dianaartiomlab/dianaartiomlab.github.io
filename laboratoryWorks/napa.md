---
layout: default
title: APA
---

#Laboratory work Nr. 2

###Merge Sort Method
```
def mergeSort(_list):
    print("Splitting ",_list)
    if len(_list)>=2:
        mid = len(_list)//2
        firstHalf = _list[:mid]
        secondHalf = _list[mid:]

        mergeSort(firstHalf)
        mergeSort(secondHalf)

        i=0
        j=0
        index=0
        while i < len(firstHalf) and j < len(secondHalf):
            if firstHalf[i] < secondHalf[j]:
                _list[index]=firstHalf[i]
                i=i+1
            else:
                _list[index]=secondHalf[j]
                j=j+1
            index+=1

        while i < len(firstHalf):
            _list[index]=firstHalf[i]
            i=i+1
            index+=1

        while j < len(secondHalf):
            _list[index]=secondHalf[j]
            j=j+1
            index+=1
    print("Merging ",_list)

list = [32,211,93,14,56,32,29,43,20]
mergeSort(list)
print(list)

```

####Results:
Splitting  [32, 211, 93, 14, 56, 32, 29, 43, 20]<br/>
Splitting  [32, 211, 93, 14]<br/>
Splitting  [32, 211]<br/>
Splitting  [32]<br/>
Merging  [32]<br/>
Splitting  [211]<br/>
Merging  [211]<br/>
Merging  [32, 211]<br/>
Splitting  [93, 14]<br/>
Splitting  [93]<br/>
Merging  [93]<br/>
Splitting  [14]<br/>
Merging  [14]<br/>
Merging  [14, 93]<br/>
Merging  [14, 32, 93, 211]<br/>
Splitting  [56, 32, 29, 43, 20]<br/>
Splitting  [56, 32]<br/>
Splitting  [56]<br/>
Merging  [56]<br/>
Splitting  [32]<br/>
Merging  [32]<br/>
Merging  [32, 56]<br/>
Splitting  [29, 43, 20]<br/>
Splitting  [29]<br/>
Merging  [29]<br/>
Splitting  [43, 20]<br/>
Splitting  [43]<br/>
Merging  [43]<br/>
Splitting  [20]<br/>
Merging  [20]<br/>
Merging  [20, 43]<br/>
Merging  [20, 29, 43]<br/>
Merging  [20, 29, 32, 43, 56]<br/>
Merging  [14, 20, 29, 32, 32, 43, 56, 93, 211]<br/>
[14, 20, 29, 32, 32, 43, 56, 93, 211]<br/><br/>

###Quick Sort Method
```
def quickSort(_list):
   quickSortHelper(_list,0,len(_list)-1)

def quickSortHelper(_list,first,last):
   if first<last:

       splitpoint = partition(_list,first,last)
       quickSortHelper(_list,first,splitpoint-1)
       quickSortHelper(_list,splitpoint+1,last)


def partition(_list,first,last):
   pivotvalue = _list[first]

   leftmark = first+1
   rightmark = last

   done = False
   while not done:

       while leftmark <= rightmark and _list[leftmark] <= pivotvalue:
           leftmark = leftmark + 1

       while _list[rightmark] >= pivotvalue and rightmark >= leftmark:
           rightmark = rightmark -1

       if rightmark < leftmark:
           done = True
       else:
           temp = _list[leftmark]
           _list[leftmark] = _list[rightmark]
           _list[rightmark] = temp

   temp = _list[first]
   _list[first] = _list[rightmark]
   _list[rightmark] = temp


   return rightmark

list = [32,211,93,14,56,32,29,43,20]
quickSort(list)
print(list)

```

####Results:
[14, 20, 29, 32, 32, 43, 56, 93, 211]<br/>

<div class="custom-image"><img src="http://www.csee.umbc.edu/~chang/cs202.s98/lectures/lec06/mvq.gif" /></div>

##Conclusion:
By performing this laboratory work we learned how to work with mergesort and quicksort algorithms. What can be said is that while quicksort is often a better choice than merge sort, there are definitely times when merge sort is thereotically a better choice. The most obvious time is when it's extremely important that your algorithm run faster than O(n^2). Quicksort is usually faster than this, but given the theoretical worst possible input, it could run in O(n^2), which is worse than the worst possible merge sort.

Quicksort is also more complicated than mergesort, especially if you want to write a really solid implementation, and so if you're aiming for simplicity and maintainability, merge sort becomes a promising alternative with very little performance loss.

```

#Laboratory work Nr. 1

###Ex.1
```
from math import *
from time import time
import matplotlib.pyplot as plt

#here is the firs(recursion) method
n = 10
n2 = 10
def fibonacci_rec(n):
    if n < 2:
        return n
    else:
        return fibonacci_rec(n-1) + fibonacci_rec(n-2)

def f1(n):
    startTime = time()
    fibonacci_rec(n)
    return time() - startTime

#here is the second mehtod(using loop)
def fibonacci_for(n):
    i = 1
    j = 0
    for k in range(n):
        j = i + j
        i = j - i
    return j

def f2(n2):
    startTime = time()
    fibonacci_for(n2)
    return time() - startTime

#here is the code in function 3
def fibonacci_third(n):
    i = 1
    j = 0
    k = 0
    h = 1
    while (n > 0):
        if n % 2 != 0:
            t = j * h
            j = i * h + j * k + t
            i = i * k + t
        t = h * h
        h = 2 * k * h + t
        k = k * k + t
        n = n / 2
    return j

def f3(n2):
    startTime = time()
    fibonacci_third(n2)
    return time() - startTime
def timeMeasure(func):
    startTime = time()
    a = func
    return time() - startTime

A = []
C = []
B = []

for i in range(15):
    A.append(f1(i))
    B.append(f2(i))
    C.append(f3(i))


plt.plot(A)
plt.plot(C)
plt.plot(B)
plt.show()

```
<div class="custom-image"><img src="https://40.media.tumblr.com/ae6ad8b1aeab2d26085a7b4653a37e9a/tumblr_nw6dys7zk31udztn8o1_540.png" /></div>

##Conclusion
By analyzing the results it can be reasonably said that the algorithms don't have the same complexity. The thing is, in a given interval of time, the algorithms converge in a different way. 
When doing the recursive implementation of fibonacci algorithm, you are adding redundant calls by recomputing the same values over and over again. 
Iterative functions – are loop based imperative repetitions of a process (in contrast to recursion which has a more declarative approach).
This is the main difference between these approaches. <br />
P.S. There are lots of algorithms for computing fibonacci that can be found on google.
