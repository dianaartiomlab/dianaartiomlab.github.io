---
layout: default
title: APA
---

#Laboratory work Nr. 3

### Kruskal Algorithm
Kruskal's algorithm is a minimum-spanning-tree algorithm which finds an edge of the least possible weight that connects any two trees in the forest. It is a greedy algorithm in graph theory as it finds a minimum spanning tree for a connected weighted graph adding increasing cost arcs at each step. This means it finds a subset of the edges that forms a tree that includes every vertex, where the total weight of all the edges in the tree is minimized. If the graph is not connected, then it finds a minimum spanning forest (a minimum spanning tree for each connected component).
<br />
The same principle is represented in the following image:

<div class="custom-image"><img src="https://www.tumblr.com/blog/ggitrn#" /></div>

Next, follows the code implementation:
```
parent = dict()
rank = dict()

def make_set(vertice):
    parent[vertice] = vertice
    rank[vertice] = 0

def find(vertice):
    if parent[vertice] != vertice:
        parent[vertice] = find(parent[vertice])
    return parent[vertice]

def union(vertice1, vertice2):
    root1 = find(vertice1)
    root2 = find(vertice2)
    if root1 != root2:
        if rank[root1] > rank[root2]:
            parent[root2] = root1
        else:
            parent[root1] = root2
            if rank[root1] == rank[root2]: rank[root2] += 1

def kruskal(graph):
    for vertice in graph['vertices']:
        make_set(vertice)

    minimum_spanning_tree = set()
    edges = list(graph['edges'])
    edges.sort()
    for edge in edges:
        weight, vertice1, vertice2 = edge
        if find(vertice1) != find(vertice2):
            union(vertice1, vertice2)
            minimum_spanning_tree.add(edge)
    return minimum_spanning_tree

graph = {
        'vertices': ['A', 'B', 'C', 'D', 'E', 'F'],
        'edges': set([
            (1, 'A', 'B'),
            (5, 'A', 'C'),
            (3, 'A', 'D'),
            (4, 'B', 'C'),
            (2, 'B', 'D'),
            (1, 'C', 'D'),
            ])
        }

print kruskal(graph)

```

##Conlusion:
Kruskal's algorithm is pretty simple. Intuitively, it collects the cheapest eligible edges which bolsters the belief that the "minimum" part in the caption (Minimum Spanning Tree) may well be justified. The algorithm avoids loops maintaining at every stage a forest of a finite number of trees. The number of trees can't grow indefinitely so that one may expect that, with time, some trees will be bridged into a single tree until only one tree remains. 

###Floyd Algorithm
The Floyd–Warshall algorithm is an algorithm for finding shortest paths in a weighted graph with positive or negative edge weights (but with no negative cycles). A single execution of the algorithm will find the lengths (summed weights) of the shortest paths between all pairs of vertices, though it does not return details of the paths themselves. 

###Python code of the program:
```
import math


def printSolution(distGraph):
    string = "inf"
    nodes =distGraph.keys()
    for n in nodes:
        print "\t%6s"%(n),
    print " "
    for i in nodes:
        print"%s"%(i),
        for j in nodes:
            if distGraph[i][j] == INF:
                print "%10s"%(string),
            else:
                print "%10s"%(distGraph[i][j]),
        print" "

def floydWarshall(graph):
    nodes = graph.keys()
    distance = {}
    for n in nodes:
        distance[n] = {}
        for k in nodes:
            distance[n][k] = graph[n][k]
    for k in nodes:
        for i in nodes:
            for j in nodes:
                if distance[i][k] + distance[k][j] < distance[i][j]:
                    distance[i][j] = distance[i][k]+distance[k][j]
    printSolution(distance)

INF = 999999999
if __name__ == '__main__':
    graph = {'A':{'A':0,'B':6,'C':INF,'D':6,'E':7},
             'B':{'A':INF,'B':0,'C':5,'D':INF,'E':INF},
             'C':{'A':INF,'B':INF,'C':0,'D':9,'E':3},
             'D':{'A':INF,'B':INF,'C':9,'D':0,'E':7},
             'E':{'A':INF,'B':4,'C':INF,'D':INF,'E':0}
             }

floydWarshall(graph)
```

##Conclusion:
A shortest path problem can be easily solved by using the Floyd Algorithm. It is not very complicated, talking prom implementable point of view, but is very efficient. The above program only prints the shortest distances. We can modify the solution to print the shortest paths also by storing the predecessor information in a separate 2D matrix.
Also, the value of INF can be taken as INT_MAX from limits.h to make sure that we handle maximum possible value. When we take INF as INT_MAX, we need to change the if condition in the above program to avoid arithmatic overflow.

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
