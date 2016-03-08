---
layout: default
title: Operations Research
---

#Laboratory work Nr. 1

###Advertisement budget optimisation

The advertising alternatives for a company includes television, radio, newspaper and internet. The cost and estimates for audience coverage are given in table bellow. The local newspaper limits the number of weekly advertisements from a single company to five. Moreover, in order to balance the advertising among the four types of media, no more than 30% of the total number of advertisements should occur on the internet and at least 10% should occur on TV. The weekly advertising budget is 20 000$. How many advertisements should be run in each of the type of the media to maximize the total audience?

<table>
    <tr>
        <th>  </th>
        <th>Television</th>
        <th>Newspaper</th>
        <th>Radio</th>
        <th>Online Advertising</th>
    </tr>
    <tr>
        <td>Cost per advertisment</td>
        <td>2000$</td>
        <td>600$</td>
        <td>300$</td>
        <td>10$</td>
    </tr>
    <tr>
        <td>Audience per advertising</td>
        <td>100 000</td>
        <td>40 000</td>
        <td>18 000</td>
        <td>1000</td>
    </tr>
</table> 

Use Solver add-in provided by Excel or Open Office Calc application for finding out the solution. Please examine additionally three other scenarios with different numbers, for example more expensive TV advertising and less restrictive budget balancing rule, and see how the optimal distribution of the budget changes. Comment your result.

######Work process:
First of all, I formulated the mathematical model of the problem. Assuming that<br />
x1 = Nr. of advertisements for television<br />
x2 = Nr. of advertisements for newspaper<br />
x3 = Nr. of advertisements for radion<br />
x4 = Nr. of advertisements for Internet <br />

and using the constrains from the problem I obtained the following system of inequalities:

2000x1 + 600x2 + 300x3 + x4 <= 20 000<br />
-9x1 + x2 + x3 + x4 <= 0<br />
-3x1 - 3x2 - 3x3 + 7x4 <= 0<br />
x_3 <= 5<br />

and the Objective function:<br />

Z = 100000x1 + 40000x2 + 18000x3 + 1000x4

In excel, I represented the data in the following way:
<div class="custom-image"><img src="https://36.media.tumblr.com/577525c2dc82a773e9484c6d3152862d/tumblr_o3pkzxwNM61udztn8o6_500.png" /></div>

Same model was used for other different data:
<div class="custom-image"><img src="https://41.media.tumblr.com/2503aeaaa14b54196bcd20548c336468/tumblr_o3pkzxwNM61udztn8o7_500.png" /></div>
<div class="custom-image"><img src="https://40.media.tumblr.com/75dbb29a1c8872a2cfed7c25f1e5d791/tumblr_o3pkzxwNM61udztn8o10_500.png" /></div>

In order to solve the problem, I used the Solver:
<div class="custom-image"><img src="https://40.media.tumblr.com/ac3dfecb86cfc501f0aa1f025519d43a/tumblr_o3pkzxwNM61udztn8o3_1280.png" /></div>

####Revelations: ))
First of all, I lost a lot of time, trying to undestand why my result differed from my group mates, I obtaine smth like... floating point numers. Which is not okay. I only should have intefer numbers when dealing with "number of pieces"(related to the number of each advertisement type). To solve this issue I added the constraint for the changing cells - to accept only integer values. I made sure, that it is "intelligent" conversion to int. I mean, not just to round, but to round such that the result will be in accordance to the maximum solution.

###Shortest path in a grapth
Using Excel solver with simplex method find the shortes path from the point 1 to point 10 in the graph bellow. Write the constraints and the function that you chosed to be optimized. Please write all, if any, interesting properties you’ve noticed when writting down the constraints. Find the shortest path using linear programming solver from Open Office or Excel.

<br />
The Excel model, for this problem, looks in the following way:

<div class="custom-image"><img src="https://41.media.tumblr.com/ffb9bdcbaf4775f42b3b7be58e93e083/tumblr_o3pkzxwNM61udztn8o5_500.png" /></div>
Moreover, below the colums From, To, Cost, Go, Net Flow, Demand, are defined names of these columns, called respectively to the column strings:
<div class="custom-image"><img src="https://36.media.tumblr.com/ae2c4f3c687482ec9623ca93b367f607/tumblr_o3pl0nYsBy1udztn8o1_1280.png" /></div>

###Conclusion:
It turns out that Excel is a really powerful instrument. It was a great wonder for me to see that using a Solver you can find out the maximum/minimum value of a function. Moreover, in excel you can solve "shortest path in a graph" problem, which is kinda cool! I`ve learned cool stuff here, and I pretty challenged to perform the next laboratory works.