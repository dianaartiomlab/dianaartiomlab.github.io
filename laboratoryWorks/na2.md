\documentclass[12pt,a4paper]{article}
\usepackage[english,romanian]{babel}
\usepackage[left=2.5cm,right = 2.5cm,top = 2.5cm, bottom = 2.5cm]{geometry}
\usepackage[utf8x]{inputenc}
\usepackage{graphicx}
\usepackage{listings}
\usepackage{enumerate}
\usepackage{hyperref}
\lstset{breaklines=true}
\renewcommand{\baselinestretch}{1.5}
\setlength{\parindent}{2em}
          % Include the listings-package

\lstset{language=Python}

\lstset{language=Python}   

\begin{document}
\begin{titlepage}
\center
\textsc{ MINISTERUL EDUCAȚIEI REPUBLICII MOLDOVA}\\
\textbf{UNIVERSITATEA TEHNICĂ A MOLDOVEI}\\
\textbf{Facultatea "Calculatoare, informatică și microelectronică"}\\
\textsc{FILIERA ANGLOFONĂ}\\[2cm]
{ \huge \bfseries RAPORT}\\[1cm] % Title of your document
\textbf{Lucrarea de laborator nr. 1}\\
\textbf{la Metode Numerice}\\[5cm]
\begin{minipage}{0.4\textwidth}
\begin{flushleft} \large
\emph{Elaborat:}\\
\emph{st. gr. FAF-141}\\
\end{flushleft}
\end{minipage}
~
\begin{minipage}{0.4\textwidth}
\begin{flushright} \large
Artiom Diana\\
\end{flushright}
\end{minipage}\\[1cm]
\begin{minipage}{0.4\textwidth}
\begin{flushleft} \large
\emph{Verificat:}\\
\emph{lect. univ.}\\
\end{flushleft}
\end{minipage}
~
\begin{minipage}{0.4\textwidth}
\begin{flushright} \large
Torică Eugen
\end{flushright}
\end{minipage}\\[4.5cm]
{\large Chișinău}\\
2015\\[3cm] % Date, change the \today to a set date if you want to be precise
\vfill % Fill the rest of the page with whitespace
\end{titlepage}
\newpage
\section*{Problem 1: Root finding}
Find the root of the function $f(x) = \sqrt x - e^{-x}$ on the interval [0, 1.2] with the error tolerance of 10^{-4}. 
a) Apply the bisection method starting with a = 0 and b = 1.2.
b) Apply the false position method starting with a = 0 and b = 1.2.
For each method compute also the absolute errors $|x - x*|$ for each iterate.  
\section*{Part A}
\begin{lstlisting}
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

bisection(func, 0, 1.2, tol=0.0001,max_it=100)
\end{lstlisting}
\section*{Results:}
n=1 a=0.00000000  b=1.20000000 mid=0.60000000 f(mid)=0.22578503\\
n=2 a=0.00000000  b=0.60000000 mid=0.30000000 f(mid)=-0.19309566\\
n=3 a=0.30000000  b=0.60000000 mid=0.45000000 f(mid)=0.03319224\\
n=4 a=0.30000000  b=0.45000000 mid=0.37500000 f(mid)=-0.07491684\\
n=5 a=0.37500000  b=0.45000000 mid=0.41250000 f(mid)=-0.01973157\\
n=6 a=0.41250000  b=0.45000000 mid=0.43125000 f(mid)=0.00699981\\
n=7 a=0.41250000  b=0.43125000 mid=0.42187500 f(mid)=-0.00629696\\
n=8 a=0.42187500  b=0.43125000 mid=0.42656250 f(mid)=0.00036846\\
n=9 a=0.42187500  b=0.42656250 mid=0.42421875 f(mid)=-0.00295997\\
n=10 a=0.42421875 b=0.42656250 mid=0.42539062 f(mid)=-0.00129469\\
n=11 a=0.42539062 b=0.42656250 mid=0.42597656 f(mid)=-0.00046285\\
n=12 a=0.42597656 b=0.42656250 mid=0.42626953 f(mid)=-0.00004713\\
n=13 a=0.42626953 b=0.42656250 mid=0.42641602 f(mid)=0.00016068\\
n=14 a=0.42626953 b=0.42641602 mid=0.42634277 f(mid)=0.00005678\\

number of iterations = 1
\section*{Part B}
\begin{lstlisting}
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

check = falsePosMethod(func, 0.8, 1)
print check
\end{lstlisting}
\section*{Results:}
0.426243709669
\section*{Conclusion:}
After implementting the rootfindigs methods we can analyze their behaviour and the way they converge to the real root. As we observe, bisection method coverges really slow to the real root. Bisection method never diverges from the root but always converges to the root. However, the convergence process may take a lot of iterations and takes a very long interval of time. 
The second method seems to be more appropriate as it does not need such a bunch if iterations to get same result. In conclusion, false position method seems to be more appropriate in solving this problem.

\section*{Problem2 - Big Bank of Ionland}
Big Bank in Ionland is launching a new promo campaign on it`s new "Unbelievable offer" for mortgages. You are an ordinary citizen in Ionland with a good job which pays you a good salary. You are young, beautiful and healthy and consider to have a family and since every family should have it`s own nest you are interested in the offer. The only thing that is missing from the picture is how much actually should you pay each month. A typical mortgage loan will consist of an amount a that is borrowed at an anual interest rate of r\% for n years. Show that if the borrower makes a monthly payment of p ionian dolars, then the total amount left to pay after n years is 
$$a(1+r)^n - \sum\limits_{i=0}^{12*n-1} p(1+r/12)^i = a(1 + r)^n - p\frac{(1+r/12)^{12n}-1}{r/12}$$
\section*{Part A}
\begin{lstlisting}
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
\end{lstlisting}

\section*{Results:}
After 1 months, remains to pay 49340.00 dollars.
After 2 months, remains to pay 48679.47 dollars.
After 3 months, remains to pay 48018.42 dollars.
After 4 months, remains to pay 47356.83 dollars.
After 5 months, remains to pay 46694.72 dollars.
After 6 months, remains to pay 46032.07 dollars.
After 7 months, remains to pay 45368.90 dollars.
After 8 months, remains to pay 44705.19 dollars.
After 9 months, remains to pay 44040.96 dollars.
After 10 months, remains to pay 43376.19 dollars.
After 11 months, remains to pay 42710.89 dollars.
After 12 months, remains to pay 42045.06 dollars.
After 13 months, remains to pay 41378.69 dollars.
After 14 months, remains to pay 40711.80 dollars.
After 15 months, remains to pay 40044.37 dollars.
After 16 months, remains to pay 39376.40 dollars.
After 17 months, remains to pay 38707.90 dollars.
After 18 months, remains to pay 38038.87 dollars.
After 19 months, remains to pay 37369.30 dollars.
After 20 months, remains to pay 36699.20 dollars.
After 21 months, remains to pay 36028.56 dollars.
After 22 months, remains to pay 35357.38 dollars.
After 23 months, remains to pay 34685.66 dollars.
After 24 months, remains to pay 34013.41 dollars.
After 25 months, remains to pay 33340.62 dollars.
After 26 months, remains to pay 32667.30 dollars.
After 27 months, remains to pay 31993.43 dollars.
After 28 months, remains to pay 31319.03 dollars.
After 29 months, remains to pay 30644.08 dollars.
After 30 months, remains to pay 29968.60 dollars.
After 31 months, remains to pay 29292.57 dollars.
After 32 months, remains to pay 28616.00 dollars.
After 33 months, remains to pay 27938.90 dollars.
After 34 months, remains to pay 27261.25 dollars.
After 35 months, remains to pay 26583.06 dollars.
After 36 months, remains to pay 25904.32 dollars.
After 37 months, remains to pay 25225.05 dollars.
After 38 months, remains to pay 24545.23 dollars.
After 39 months, remains to pay 23864.86 dollars.
After 40 months, remains to pay 23183.96 dollars.
After 41 months, remains to pay 22502.50 dollars.
After 42 months, remains to pay 21820.50 dollars.
After 43 months, remains to pay 21137.96 dollars.
After 44 months, remains to pay 20454.87 dollars.
After 45 months, remains to pay 19771.24 dollars.
After 46 months, remains to pay 19087.05 dollars.
After 47 months, remains to pay 18402.32 dollars.
After 48 months, remains to pay 17717.04 dollars.
After 49 months, remains to pay 17031.22 dollars.
After 50 months, remains to pay 16344.84 dollars.
After 51 months, remains to pay 15657.92 dollars.
After 52 months, remains to pay 14970.44 dollars.
After 53 months, remains to pay 14282.42 dollars.
After 54 months, remains to pay 13593.85 dollars.
After 55 months, remains to pay 12904.72 dollars.
After 56 months, remains to pay 12215.05 dollars.
After 57 months, remains to pay 11524.82 dollars.
After 58 months, remains to pay 10834.04 dollars.
After 59 months, remains to pay 10142.71 dollars.
After 60 months, remains to pay 9450.82 dollars.
After 61 months, remains to pay 8758.38 dollars.
After 62 months, remains to pay 8065.39 dollars.
After 63 months, remains to pay 7371.84 dollars.
After 64 months, remains to pay 6677.74 dollars.
After 65 months, remains to pay 5983.08 dollars.
After 66 months, remains to pay 5287.86 dollars.
After 67 months, remains to pay 4592.10 dollars.
After 68 months, remains to pay 3895.77 dollars.
After 69 months, remains to pay 3198.89 dollars.
After 70 months, remains to pay 2501.44 dollars.
After 71 months, remains to pay 1803.45 dollars.
After 72 months, remains to pay 1104.89 dollars.
After 73 months, remains to pay 405.77 dollars.
After 74 months, remains to pay -293.90 dollars.
74

\section*{Part B}
\begin{lstlisting}
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

check = secant(func, 0.08, 1)
print(check)
\end{lstlisting}
\section{Results:}
According to secant method we`ve learnt at Mr Boston`s lectures, the yearly payments for the loan to be paid in 20 years at
8\% interest is: 10185.2208823\$
\section{Part C}
\begin{lstlisting}
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

check = secant(func1, 0.8, 1)
print(check)
\end{lstlisting}
\section{Results:}
The interest rate required for the loan to be paid in 20 years is 0.077546898357042
that is somewhere 7.7\%.

\newpage


\end{document}
