---
layout: default
title: Operations Research
---
#Laboratory work Nr. 2

###Maximal Flow problem
####Condition of the Problem
Using Excel solver, or any other software, find the Max-Flow value for the network between source point 1 and destination point 8. Nework is shown in the image below. Value on the edge shows maximum number of units that can be transported on a given path between two vertices. Report should contain the constraints and the function that you chose to be optimized. <br />
Basically, that`s how the graph looks like:

<div class="custom-image"><img src="https://41.media.tumblr.com/b9df34a08c70e2548fa8922c54b208e5/tumblr_o5fukuZ1Si1rl36tko1_500.png" /></div>
In order to solve the problem I used the excel solver. So, asically the following image describes perfectly the way I solved the problem:

<div class="custom-image"><img src="https://36.media.tumblr.com/265647f8d318aec5df02f277602feb81/tumblr_o5fusvmDRN1udztn8o3_1280.png" /></div>

For making my life easier I defined some names:

<div class="custom-image"><img src="https://41.media.tumblr.com/dc3f432a7f8301b1565910940278dc01/tumblr_o5fusvmDRN1udztn8o1_1280.png" /></div>

The solver has the following subject to constrains:

<div class="custom-image"><img src="https://41.media.tumblr.com/70954600342ffe064bcca2f6dd298e16/tumblr_o5fusvmDRN1udztn8o2_1280.png" /></div>

Actually, solved proved itself to be also a better solution in maximal flow finding problems, as it is very easy and comfortable to use. <br />

A bit more complicated task was to create a program to find the maximal flow problem, by using the Ford-Fulkerson algorithm.
Next, follows the program code.

```
# definition of edge class
class Edge(object):
    def __init__(self, u, v, w):
        self.source = u
        self.destination = v
        self.capacity = w
    def __repr__(self):
        return "%s->%s:%s" % (self.source, self.destination, self.capacity)


class FlowNetwork():
    def __init__(self):
        self.directions = {}
        self.flow = {}

    # function to add a vertex
    def add_vertex(self, vertex):
        self.directions[vertex] = []

    # returns the edges connected to a specific vertex
    def get_edges(self, v):
        return self.directions[v]

    # adds a new edge
    def add_edge(self, u, v, w=0):
        if u == v:
            raise ValueError("u == v")
        edge = Edge(u,v,w)
        redge = Edge(v,u,0)
        edge.redge = redge #redge is not defined in Edge class
        redge.redge = edge
        self.directions[u].append(edge)
        self.directions[v].append(redge)
        self.flow[edge] = 0
        self.flow[redge] = 0


    # fing a path
    def find_path(self, source, destination, path, path_set):
        if source == destination: # make sure starting vertex doesn`t match the end one
            return path
        for edge in self.get_edges(source):
            residual = edge.capacity - self.flow[edge] # compute the residual value
            if residual > 0 and not (edge,residual) in path_set:
                path_set.add((edge, residual))
                result = self.find_path( edge.destination, destination, path + [(edge,residual)], path_set)
                if result != None:
                    return result

    # compute maximal flow
    def max_flow(self, source, destination):
        path = self.find_path(source, destination, [], set())
        while path != None:
            flow = min(res for edge,res in path)
            for edge,res in path:
                self.flow[edge] += flow 
                self.flow[edge.redge] -= flow
            path = self.find_path(source, destination, [], set())
        return sum(self.flow[edge] for edge in self.get_edges(source))


# definitio of graph object, an instance of FlowNetwork class
graph = FlowNetwork()
[graph.add_vertex(v) for v in "12345678"] # iteratively, add each vertex

# addition ow each edge to the graph, in accordance to the condition of the problem
graph.add_edge('1', '2', 16)
graph.add_edge('1', '3', 13)
graph.add_edge('2', '3', 4)
graph.add_edge('2', '4', 12)
graph.add_edge('3', '2', 10)
graph.add_edge('3', '5', 14)
graph.add_edge('3', '7', 5)
graph.add_edge('4', '3', 9)
graph.add_edge('4', '6', 20)
graph.add_edge('5', '4', 7)
graph.add_edge('5', '6', 8)
graph.add_edge('5', '7', 3)
graph.add_edge('6', '7', 5)
graph.add_edge('6', '8', 12)
graph.add_edge('7', '8', 18)

# print the solution
print graph.max_flow('1','8')
```

Very strange, but the solution matches the one obtained using Excel Solver.. Hmmm, what a mistery ))

<div class="custom-image"><img src="https://40.media.tumblr.com/07261f77d0bef468b10074aa7ca368ea/tumblr_o5h8mz7noH1udztn8o1_400.png" /></div>

####Conclusion:
It turns out that Ford-Fulkerson is conceptually a straightforward algorithm for solving the maximum flow problem.
But what`s the main idea? So basically here it is: keep adding augumenting paths until there are no more. It is very useful, and when you have a network problem which states in finding the max flow, the most thing u will like to do is to use the Ford-Fulkerson algorithm.

#Laboratory work Nr. 1

###Advertisement budget optimisation

The advertising alternatives for a company includes television, radio, newspaper and internet. The cost and estimates for audience coverage are given in table bellow. The local newspaper limits the number of weekly advertisements from a single company to five. Moreover, in order to balance the advertising among the four types of media, no more than 30% of the total number of advertisements should occur on the internet and at least 10% should occur on TV. The weekly advertising budget is 20 000$. How many advertisements should be run in each of the type of the media to maximize the total audience?

<table>
    <tr>
        <th>  </th>
        <th>Television</th>
        <th>Newspaper</th>
        <th>Radio</th>
        <th>Online</th>
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

The constrains were set in the following way:
For the first equation: <br />
2000x1 + 600x2 + 300x3 + x4 <= 20 000<br />
I used the function SUMPRODUCT. As parameters - first - "Cost per advertising" row in the table, and second - the first row in "Equation parameters" section.
Same was logic was applied for the other constrains.

####Revelations: ))
First of all, I lost a lot of time, trying to undestand why my result differed from my group mates, I obtaine smth like... floating point numers. Which is not okay. I only should have intefer numbers when dealing with "number of pieces"(related to the number of each advertisement type). To solve this issue I added the constraint for the changing cells - to accept only integer values. I made sure, that it is "intelligent" conversion to int. I mean, not just to round, but to round such that the result will be in accordance to the maximum solution.

###Shortest path in a grapth
Using Excel solver with simplex method find the shortes path from the point 1 to point 10 in the graph bellow. Write the constraints and the function that you chosed to be optimized. Please write all, if any, interesting properties you’ve noticed when writting down the constraints. Find the shortest path using linear programming solver from Open Office or Excel.

<br />
The Excel model, for this problem, looks in the following way:

<div class="custom-image"><img src="https://41.media.tumblr.com/ffb9bdcbaf4775f42b3b7be58e93e083/tumblr_o3pkzxwNM61udztn8o5_500.png" /></div>
Moreover, below the colums From, To, Cost, Go, Net Flow, Demand, are defined names of these columns, called respectively to the column strings:
<div class="custom-image"><img src="https://36.media.tumblr.com/ae2c4f3c687482ec9623ca93b367f607/tumblr_o3pl0nYsBy1udztn8o1_1280.png" /></div>

In order to perform the work, I used the SUMIF functions to calculate the Net Flow of each node.

###Conclusion:
It turns out that Excel is a really powerful instrument. It was a great wonder for me to see that using a Solver you can find out the maximum/minimum value of a function. Moreover, in excel you can solve "shortest path in a graph" problem, which is kinda cool! I`ve learned cool stuff here, and I pretty challenged to perform the next laboratory works.