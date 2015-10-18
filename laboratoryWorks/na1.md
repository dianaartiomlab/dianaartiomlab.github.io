---
layout: default
title: Numerical Analysis
---

##Laboratory work No. 3
###Problem 1: Root finding

####Newton`s method
```
# first porblem
from math import *

def f(x):
    return sqrt(x) - exp(-x)

def derivative(x):
    return 1.0 / (2 * sqrt(x)) - 1

# Newton`s method
def newtonMethod(f, derivative, x0, tolerance = 0.0001, maxIter = 100):
    n = 1
    print ("\n")
    while n <= maxIter:
        x1 = f(x0) - f(x0) / derivative(x0)
        print ("n = %d, Xn = %.8f, Xn+1 - Xn = %.8f, f(x+1) = %.8f") % (n, x0, x1 - x0, f(x1))
        
        if abs(x1 - x0) < tolerance:
            print "Number of iterations: ", n
            return x1
        else:
            n = n + 1
            x0 = x1
    return False
```
####Results:

n = 1, Xn = 0.60000000, Xn+1 - Xn = 0.26269128, f(x+1) = 0.50678699<br />
n = 2, Xn = 0.86269128, Xn+1 - Xn = 0.74180283, f(x+1) = 1.06569506<br />
n = 3, Xn = 1.60449411, Xn+1 - Xn = 1.22189676, f(x+1) = 1.62196112<br />
n = 4, Xn = 2.82639087, Xn+1 - Xn = 1.10411217, f(x+1) = 1.96291584<br />
n = 5, Xn = 3.93050304, Xn+1 - Xn = 0.65733542, f(x+1) = 2.13174918<br />
n = 6, Xn = 4.58783846, Xn+1 - Xn = 0.32482185, f(x+1) = 2.20909929<br />
n = 7, Xn = 4.91266031, Xn+1 - Xn = 0.14904564, f(x+1) = 2.24348879<br />
n = 8, Xn = 5.06170595, Xn+1 - Xn = 0.06633308, f(x+1) = 2.25858922<br />
n = 9, Xn = 5.12803903, Xn+1 - Xn = 0.02914138, f(x+1) = 2.26518471<br />
n = 10, Xn = 5.15718041, Xn+1 - Xn = 0.01273111, f(x+1) = 2.26805887<br />
n = 11, Xn = 5.16991152, Xn+1 - Xn = 0.00554847, f(x+1) = 2.26931012<br />
n = 12, Xn = 5.17545999, Xn+1 - Xn = 0.00241559, f(x+1) = 2.26985460<br />
n = 13, Xn = 5.17787558, Xn+1 - Xn = 0.00105118, f(x+1) = 2.27009150<br />
n = 14, Xn = 5.17892676, Xn+1 - Xn = 0.00045734, f(x+1) = 2.27019455<br />
n = 15, Xn = 5.17938411, Xn+1 - Xn = 0.00019896, f(x+1) = 2.27023939<br />
n = 16, Xn = 5.17958307, Xn+1 - Xn = 0.00008655, f(x+1) = 2.27025889<br />
Number of iterations:  16


####Newton`s simplified
```

# Newton`s simplified method
def newtonSimplifMethod(f, x0, tolerance = 0.0001, maxIter = 100):
    n = 1
    print ("\n")
    while n <= maxIter:
        x1 = x0 - f(x0) / ((f(x0 + f(x0)) - f(x0)) / f(x0)) 
        print ("n = %d, Xn = %.8f, Xn+1 - Xn = %.8f, f(x+1) = %.8f") % (n, x0, x1 - x0, f(x1))
        
        if abs(x1 - x0) < tolerance:
            print "Number of iterations: ", n
            return x1
        else:
            n = n + 1
            x0 = x1
    return False

```
####Results:
n = 1, Xn = 0.60000000, Xn+1 - Xn = -0.20803375, f(x+1) = -0.04965483<br />
n = 2, Xn = 0.39196625, Xn+1 - Xn = 0.03270102, f(x+1) = -0.00232234<br />
n = 3, Xn = 0.42466728, Xn+1 - Xn = 0.00163193, f(x+1) = -0.00000503<br />
n = 4, Xn = 0.42629921, Xn+1 - Xn = 0.00000354, f(x+1) = -0.00000000<br />
Number of iterations:  4


####Secant method
```
# Secant method
def secant(f, x0, x1, tol=0.0001, maxIt=100):
    n = 1
    print("\n")
    while n <= maxIt:
        x2 = x1 - f(x1) * ((x1 - x0) / (f(x1) - f(x0)))
        print(("n = %d, Xn = %.8f, Xn+1 = %.8f, root = %.8f, f(root) = %.8f") % (n - 1, x0, x1, x2, f(x2)))
        if abs(x2 - x1) < tol:
            print "\nNumber of iterations =", n
            return x2
        else:
            n = n + 1
            x0 = x1
            x1 = x2
    return False

```
####Results:
n = 1, Xn = 0.60000000, Xn+1 - Xn = -0.20803375, f(x+1) = -0.04965483<br />
Number of iterations:  1

###Conclusion:
By implementing each rootfinding method we can analyze their behaviour and the way they converge to the real root.Therefore we see that the rate of convergence of Newton , simplified Newton and secant method is greater. Here are the results for f(x) in estimated root . We see that newton’s method gave the best approximation for the real root , because it is closer to 0.0 than others.

###Problem 2: Root finding


```
import math

def func1(x):
    return 2 * math.exp(-x)

def func2(x):
    return 0.9 / ( 1 + x ** 4)

def func3(x):
    return 6.28 + math.sin(x)

def fixed(f, x0, tol = 0.000001, max_it=1000):
    n=1
    while n <= max_it:
        x1 = f(x0)
        if (abs(x1 - x0) < tol):
            print("Root is =", x1)
            print("Number of iterations =", n)
            return
        else:
            x0 = x1
            n = n + 1


def aitken(f, x0, tol = 0.000001, max_it=100):
    n = 1
    while n <= max_it:
        x1 = f(x0)
        x2 = f(x1)
        app_x2 = x2 - ((x2 - x1) **2) / ((x2 - x1) - (x1 - x0))
        lambda_a = (x2 - x1) / (x1 - x0)
        print(("n=%d, Xn=%f, lambda=%f, alfa-Xn=%f") % (n - 1, x0, lambda_a, lambda_a / (1 - lambda_a) * (x1 - x0)))
        if (abs(app_x2 - x2) <= tol):
            print("Root is =", app_x2, "with", n, "iterations")
            return
        else:
            x0 = app_x2
            n = n + 1
```
####Results:

Fixed: 
<br />
First function: 
('Root is =', 0.8526051018601054)
('Number of iterations =', 74)
Second function: 
('Root is =', 0.7141895972112392)
('Number of iterations =', 59)
Third funtion: 
('Root is =', 6.015529419935787)
('Number of iterations =', 388)

<br />Aiteken

Firsst function
n=0, Xn=0.800000, lambda=-0.855751, alfa-Xn=-0.045495
n=1, Xn=0.853163, lambda=-0.852570, alfa-Xn=0.000476
n=2, Xn=0.852606, lambda=-0.852605, alfa-Xn=0.000000
('Root is =', 0.8526055020137262, 'with', 3, 'iterations')
Second function
n=0, Xn=0.750000, lambda=-0.828493, alfa-Xn=0.030050
n=1, Xn=0.713729, lambda=-0.825759, alfa-Xn=-0.000380
n=2, Xn=0.714190, lambda=-0.825822, alfa-Xn=-0.000000
('Root is =', 0.7141900480718033, 'with', 3, 'iterations')
Third function
n=0, Xn=0.600000, lambda=-0.005160, alfa-Xn=-0.032057
n=1, Xn=6.812586, lambda=0.869962, alfa-Xn=-0.184443
n=2, Xn=6.600573, lambda=0.951367, alfa-Xn=-0.166028
n=3, Xn=6.426058, lambda=0.990070, alfa-Xn=-0.366013
n=4, Xn=6.056374, lambda=0.974248, alfa-Xn=-0.047126
n=5, Xn=6.008003, lambda=0.962413, alfa-Xn=0.007031
n=6, Xn=6.015309, lambda=0.964336, alfa-Xn=0.000187
n=7, Xn=6.015503, lambda=0.964387, alfa-Xn=0.000000
('Root is =', 6.015503072969342, 'with', 8, 'iterations')
<br />
###Conclusion: 
As we see from results , Aitken’s extrapolation gave more precise results in
less iterations , and the execution time of the program was increased .
<br />

##Laboratory work No. 2
###Problem 1: Root finding
Find the root of the function f(x) = sqrt x - e^(-x) on the interval [0, 1.2] with the error tolerance of 10^(-4). 
a) Apply the bisection method starting with a = 0 and b = 1.2.
b) Apply the false position method starting with a = 0 and b = 1.2.
For each method compute also the absolute errors |x - x*| for each iterate
####Part A
```
import math

#given function
def func(x):
    return math.sqrt(x)-math.exp(-x)
    
#bisection method
def bisection(f,a,b,tol=0.0001,max_it=100):
    n=1
    while n<=max_it:
        c=(a+b)/2.0
        print(("n=%d a=%.8f b=%.8f mid=%.8f f(mid)=%.8f")%(n,a,b,c,f(c)))
        if f(c)==0 or (b-a)/2<tol:
            print(("\nnumber of iterations = %d")%(n))
            return c
        else:
            n=n+1
            if f(c)*f(a)>0:
                a=c
            else:
                b=c
    return False

```
####Results:

n=1 a=0.00000000  b=1.20000000 mid=0.60000000 f(mid)=0.22578503<br />
n=2 a=0.00000000  b=0.60000000 mid=0.30000000 f(mid)=-0.19309566<br />
n=3 a=0.30000000  b=0.60000000 mid=0.45000000 f(mid)=0.03319224<br />
n=4 a=0.30000000  b=0.45000000 mid=0.37500000 f(mid)=-0.07491684<br />
n=5 a=0.37500000  b=0.45000000 mid=0.41250000 f(mid)=-0.01973157<br />
n=6 a=0.41250000  b=0.45000000 mid=0.43125000 f(mid)=0.00699981<br />
n=7 a=0.41250000  b=0.43125000 mid=0.42187500 f(mid)=-0.00629696<br />
n=8 a=0.42187500  b=0.43125000 mid=0.42656250 f(mid)=0.00036846<br />
n=9 a=0.42187500  b=0.42656250 mid=0.42421875 f(mid)=-0.00295997<br />
n=10 a=0.42421875 b=0.42656250 mid=0.42539062 f(mid)=-0.00129469<br />
n=11 a=0.42539062 b=0.42656250 mid=0.42597656 f(mid)=-0.00046285<br />
n=12 a=0.42597656 b=0.42656250 mid=0.42626953 f(mid)=-0.00004713<br />
n=13 a=0.42626953 b=0.42656250 mid=0.42641602 f(mid)=0.00016068<br />
n=14 a=0.42626953 b=0.42641602 mid=0.42634277 f(mid)=0.00005678<br />

####Part B
```
import math
def func(x):
    return math.sqrt(x)-math.exp(-x)

def falsePosMethod(f, x0, x1, tol=0.0001, max_it=100):
    n = 1
    while n<=max_it:
        a = (f(x0) * x1 - f(x1) * x0) / (f(x0) - f(x1))
        if abs(f(a) ) < tol:
            return a
        if f(a) * f(x0) < 0:
            x0 = a
        else:
            x1 = a
        n = n + 1
    return a

```
####Results:
0.426243709669

###Conclusion:
After implementting the rootfindigs methods we can analyze their behaviour and the way they converge to the real root. As we observe, bisection method coverges really slow to the real root. Bisection method never diverges from the root but always converges to the root. However, the convergence process may take a lot of iterations and takes a very long interval of time. 
The second method seems to be more appropriate as it does not need such a bunch if iterations to get same result. In conclusion, false position method seems to be more appropriate in solving this problem.

###Problem2 - Big Bank of Ionland}
Big Bank in Ionland is launching a new promo campaign on it is new "Unbelievable offer" for mortgages. You are an ordinary citizen in Ionland with a good job which pays you a good salary. You are young, beautiful and healthy and consider to have a family and since every family should have it`s own nest you are interested in the offer. The only thing that is missing from the picture is how much actually should you pay each month. A typical mortgage loan will consist of an amount a that is borrowed at an anual interest rate of r\% for n years. Show that if the borrower makes a monthly payment of p ionian dolars, then the total amount left to pay after n years is 
$$a(1+r)^n - \sum\limits_{i=0}^{12*n-1} p(1+r/12)^i = a(1 + r)^n - p\frac{(1+r/12)^{12n}-1}{r/12}$$

####Part A
```
loan = 50000
monthly_pay = 700
rate = 0.08
percentage = (loan * rate) / 100
rem = loan
months = 0
while rem > 0:
    rem = loan - monthly_pay + percentage
    loan = rem
    percentage = (loan * rate) / 100
    months = months + 1
    print(("After %d months, remains to pay %.2f dollars.") % (months,loan))
print(months)
```
####Results:
After 1 months, remains to pay 49340.00 dollars.<br />
After 2 months, remains to pay 48679.47 dollars.<br />
After 3 months, remains to pay 48018.42 dollars.<br />
After 4 months, remains to pay 47356.83 dollars.<br />
After 5 months, remains to pay 46694.72 dollars.<br />
After 6 months, remains to pay 46032.07 dollars.<br />
After 7 months, remains to pay 45368.90 dollars.<br />
After 8 months, remains to pay 44705.19 dollars.<br />
After 9 months, remains to pay 44040.96 dollars.<br />
After 10 months, remains to pay 43376.19 dollars.<br />
After 11 months, remains to pay 42710.89 dollars.<br />
After 12 months, remains to pay 42045.06 dollars.<br />
After 13 months, remains to pay 41378.69 dollars.<br />
After 14 months, remains to pay 40711.80 dollars.<br />
After 15 months, remains to pay 40044.37 dollars.<br />
After 16 months, remains to pay 39376.40 dollars.<br />
After 17 months, remains to pay 38707.90 dollars.<br />
After 18 months, remains to pay 38038.87 dollars.<br />
After 19 months, remains to pay 37369.30 dollars.<br />
After 20 months, remains to pay 36699.20 dollars.<br />
After 21 months, remains to pay 36028.56 dollars.<br />
After 22 months, remains to pay 35357.38 dollars.<br />
After 23 months, remains to pay 34685.66 dollars.<br />
After 24 months, remains to pay 34013.41 dollars.<br />
After 25 months, remains to pay 33340.62 dollars.<br />
After 26 months, remains to pay 32667.30 dollars.<br />
After 27 months, remains to pay 31993.43 dollars.<br />
After 28 months, remains to pay 31319.03 dollars.<br />
After 29 months, remains to pay 30644.08 dollars.<br />
After 30 months, remains to pay 29968.60 dollars.<br />
After 31 months, remains to pay 29292.57 dollars.<br />
After 32 months, remains to pay 28616.00 dollars.<br />
After 33 months, remains to pay 27938.90 dollars.<br />
After 34 months, remains to pay 27261.25 dollars.<br />
After 35 months, remains to pay 26583.06 dollars.<br />
After 36 months, remains to pay 25904.32 dollars.<br />
After 37 months, remains to pay 25225.05 dollars.<br />
After 38 months, remains to pay 24545.23 dollars.<br />
After 39 months, remains to pay 23864.86 dollars.<br />
After 40 months, remains to pay 23183.96 dollars.<br />
After 41 months, remains to pay 22502.50 dollars.<br />
After 42 months, remains to pay 21820.50 dollars.<br />
After 43 months, remains to pay 21137.96 dollars.<br />
After 44 months, remains to pay 20454.87 dollars.<br />
After 45 months, remains to pay 19771.24 dollars.<br />
After 46 months, remains to pay 19087.05 dollars.<br />
After 47 months, remains to pay 18402.32 dollars.<br />
After 48 months, remains to pay 17717.04 dollars.<br />
After 49 months, remains to pay 17031.22 dollars.<br />
After 50 months, remains to pay 16344.84 dollars.<br />
After 51 months, remains to pay 15657.92 dollars.<br />
After 52 months, remains to pay 14970.44 dollars.<br />
After 53 months, remains to pay 14282.42 dollars.<br />
After 54 months, remains to pay 13593.85 dollars.<br />
After 55 months, remains to pay 12904.72 dollars.<br />
After 56 months, remains to pay 12215.05 dollars.<br />
After 57 months, remains to pay 11524.82 dollars.<br />
After 58 months, remains to pay 10834.04 dollars.<br />
After 59 months, remains to pay 10142.71 dollars.<br />
After 60 months, remains to pay 9450.82 dollars.<br />
After 61 months, remains to pay 8758.38 dollars.<br />
After 62 months, remains to pay 8065.39 dollars.<br />
After 63 months, remains to pay 7371.84 dollars.<br />
After 64 months, remains to pay 6677.74 dollars.<br />
After 65 months, remains to pay 5983.08 dollars.<br />
After 66 months, remains to pay 5287.86 dollars.<br />
After 67 months, remains to pay 4592.10 dollars.<br />
After 68 months, remains to pay 3895.77 dollars.<br />
After 69 months, remains to pay 3198.89 dollars.<br />
After 70 months, remains to pay 2501.44 dollars.<br />
After 71 months, remains to pay 1803.45 dollars.<br />
After 72 months, remains to pay 1104.89 dollars.<br />
After 73 months, remains to pay 405.77 dollars.<br />
After 74 months, remains to pay -293.90 dollars.<br />
74

####Part B
```
def func(x):
    return 100000 * (1 + 0.08) ** 20 - x * ((1 + 0.08) ** 20 - 1) / 0.08
def secant(f, x0, x1, tol=0.0001, max_it = 100):
    n = 1
    while n <= 100:
        x2 = x1 - f(x1) * ((x1-x0) / (f(x1) - f(x0)))
        if (abs(x2 - x1) < tol):
            return x2
        else:
            x0 = x1
            x1 = x2
    return False
```
####Results:
According to secant method we`ve learnt at Mr Boston`s lectures, the yearly payments for the loan to be paid in 20 years at
8\% interest is: 10185.2208823\$

####Part C
```
def func1(x):
    return 100000 * (1 + x) ** 20 - 10000 * ((1 + x) ** 20 - 1) / x

def secant(f, x0, x1, tol=0.0001, max_it=100):
    n = 1
    while n <= 100:
        x2 = x1 - f(x1) * ((x1 - x0) / (f(x1) - f(x0)))
        if (abs(x2 - x1) < tol):
            return x2
        else:
            x0 = x1
            x1 = x2
    return False
```
####Results:
The interest rate required for the loan to be paid in 20 years is 0.077546898357042
that is somewhere 7.7\%.

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

