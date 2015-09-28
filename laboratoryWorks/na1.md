---
layout: default
title: Numerical Analysis
---

#Laboratory work Nr. 1

###Ex.1
```
from math import *
from decimal import *
# from decimal import Context, MAX_EMAX

#here is the code for problem 1

a = [10, 100, 1000]

getcontext().prec = 1000

def function1(x):
	a = Decimal(x) * Decimal(e) ** Decimal(x)
	b = Decimal(x ** (-2))

	f = (Decimal(a) - Decimal(b)) / (Decimal(a) + Decimal(b))

	return f

for i in range(len(a)):
	print "The result for %s simulations is: " % str(a[i])
	print function1(a[i])
```

###Ex. 2
```
from math import *

# here is the code for problem 2
c = 0.1
for x in range (15) :
	r = pow(10, (1 + 2*x/10)) - pow(10, (1+2*x*c))
	print r
```
###Ex. 3
```
from math import *
import pprint

pp = pprint.PrettyPrinter(indent = 4)

io = 1 - exp(-1)

def function(k):
	if k == 0:
		return io
	else:
		return k*function(k-1) - exp(-1)

A = []

for i in range(25):
	A.append(function(i))

pp.pprint(A)
```
###Ex. 4
```
import numpy as np
import math
import matplotlib.pyplot as plt
# definition of EscVel function
def EscVel(z,c,N):
    n = 0    
    while abs(z)<=2 and n<N:
        n += 1 
        z = z ** 2 + c
    return n
# definition of JuliaSet function
def  JuliaSet(zmax,c,N):
    x = np.linspace(-zmax,zmax, 500)
    y = np.linspace(-zmax,zmax, 500)
# matrix for storing complex numbers
    Z = []
    for i in x:
        for m in y:
            complex_nr = i + m*1j
        
            Z.append(complex_nr)
    Z = np.array(Z).reshape(500,500)      
# matrix for storing the escape velocities
    M = []
    for line in Z:
        for element in line:
            M.append(EscVel(element,c,N))
    M = np.array(M).reshape(500,500)
    return M
#definition of plot funtion
def plot(M):
    im = plt.figure().gca()
    im.imshow(M, interpolation='nearest')
    
#plotting the result
plot(JuliaSet(1,-0.297491+0.641051j, 100))
```
