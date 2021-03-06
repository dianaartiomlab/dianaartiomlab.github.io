---
layout: default
title: Operations Research
---
#Laboratory work Nr. 4
I this laboratory work we had to deal with what an A* algorithm is and how it works. Basically, there are a lot of tutorials ant information on this spread on internet, but let's anyway have a look on what it is and how to eat this.
<br />
#####According to wikipedia:
A* is an informed search algorithm, or a best-first search, meaning that it solves problems by searching among all possible paths to the solution (goal) for the one that incurs the smallest cost (least distance travelled, shortest time, etc.), and among these paths it first considers the ones that appear to lead most quickly to the solution. It is formulated in terms of weighted graphs: starting from a specificnode of a graph, it constructs a tree of paths starting from that node, expanding paths one step at a time, until one of its paths ends at the predetermined goal node.

<ul> A* has the following properties:
  <li>It is complete; it will always find a solution if it exists. </li>
  <li>It can use a heuristic to significantly speed up the process. </li>
  <li>It can have variable node to node movement costs. This can be used when some nodes are more difficult to traverse, for example you may move slower across rocky terrain or up hill.</li>
  <li>It can search in many different directions if desired.<li/>
</ul>

#####Starting the Search

Once we have simplified our search area into a manageable number of nodes, as we have done with the grid layout above, the next step is to conduct a search to find the shortest path. We do this by starting at point A, checking the adjacent squares, and generally searching outward until we find our target.

<ul> We begin the search by doing the following:
  <li>
    Begin at the starting point A and add it to an “open list” of squares to be considered. The open list is kind of like a shopping list. Right now there is just one item on the list, but we will have more later. It contains squares that might fall along the path you want to take, but maybe not. Basically, this is a list of squares that need to be checked out.  
  </li>

  <li>
    Look at all the reachable or walkable squares adjacent to the starting point, ignoring squares with walls, water, or other illegal terrain. Add them to the open list, too. For each of these squares, save point A as its “parent square”. This parent square stuff is important when we want to trace our path. It will be explained more later.  
  </li>

  <li>
    Drop the starting square A from your open list, and add it to a “closed list” of squares that you don’t need to look at again for now.
  </li>
</ul>

At this point, you should have something like the following illustration. In this illustration, the dark green square in the center is your starting square. It is outlined in light blue to indicate that the square has been added to the closed list. All of the adjacent squares are now on the open list of squares to be checked, and they are outlined in light green. Each has a gray pointer that points back to its parent, which is the starting square.

<div class="custom-image"><img src="http://www.policyalmanac.org/games/aStarT2.jpg" /></div>

####But what's the difference between Dijskstra and A* ?
Both the algorithms find the shortest distance between two nodes.

<table>
    <tr>
        <th>Parameters</th>
        <th>A* algorithm</th>
        <th>Dijskstra's</th>
    </tr>
    <tr>
        <td>Search algorithm</td>
        <td>Best First Search </td>
        <td>Greedy Best First Search </td>
    <tr>
        <td>Time Complexity</td>
        <td>Time complexity is O(n logn), n is the no. of nodes.</td>
        <td>The time complexity is O(n2). </td>
    </tr>
    <tr>
        <td>Heuristics Function </td>
        <td>Heuristic Function, f(n)=g(n)+h(n), g(n) represents the cost of the path from the starting point to the vertex n. h(n) represents the heuristic estimated cost from vertex n to the g. </td>
        <td>f(n)=g(n), g(n) represents the cost of the path from the starting point to the vertex n. Dijkstra’s Algorithm is the worst case of A star Algorithm. </td>
    </tr>
</table>


###Advantages and Disadvantages
A* is faster as compare to Dijkstra’s algorithm because it uses Best First Search whereas Dijkstra’s uses Greedy Best First Search. Dijkstra’s is Simple as compare to A*. The major disadvantage of Dijkstra’s algorithm is the fact that it does a blind search there by consuming a lot of time waste of necessary resources. Another disadvantage is that it cannot handle negative edges. This leads to acyclic graphs and most often cannot obtain the right shortest path. Dijkstra's algorithm has an order of n2 so it is efficient enough to use for relatively large problems. The major disadvantage of the algorithm is the fact that it does a blind search there by consuming a lot of time waste of necessary resources.
#####As a conclusion,
Dijkstra's is essentially the same as A*, except there is no heuristic (H is always 0). Because it has no heuristic, it searches by expanding out equally in every direction, but A* scan the area only in the direction of destination.

<br />
In order to do the task regarding to finding the shortest path using A star algorithm, I created a program in python. In order to find the so called distance to the final (end) node I implemented the following formula:

```
def getHeuristic(a, b):
    return (b[0] - a[0]) ** 2 + (b[1] - a[1]) ** 2
```

Also, there is a astar function, containing the actual implementation of the searching.

```
def astar(elementList, start, endNode):

    adjacent = [(0,1),(0,-1),(1,0),(-1,0),(1,1),(1,-1),(-1,1),(-1,-1)]

    close_set = set()
    prev = {}
    g = {start:0}
    fscore = {start:getHeuristic(start, endNode)}
    oheap = []

    heappush(oheap, (fscore[start], start))

    while oheap:
        current = heappop(oheap)[1]
        if current == endNode:
            list1 = []
            while current in prev:
                list1.append(current)
                current = prev[current]
            return list1

        close_set.add(current)
        for i, j in adjacent:
            neighbNode = current[0] + i, current[1] + j
            tentative_g_score = g[current] + getHeuristic(current, neighbNode)
            if 0 <= neighbNode[0] < elementList.shape[0]:
                if 0 <= neighbNode[1] < elementList.shape[1]:
                    if elementList[neighbNode[0]][neighbNode[1]] == 1:
                        continue
                else:
                    continue
            else:
                continue

            if neighbNode in close_set and tentative_g_score >= g.get(neighbNode, 0):
                continue

            if  tentative_g_score < g.get(neighbNode, 0) or neighbNode not in [i[1]for i in oheap]:
                prev[neighbNode] = current
                g[neighbNode] = tentative_g_score
                fscore[neighbNode] = tentative_g_score + getHeuristic(neighbNode, endNode)
                heappush(oheap, (fscore[neighbNode], neighbNode))

    return False

```

When calling:

```
print astar(nmap, (1,1), (17,17))
```
it will return the list of nodes forming the path, which in terms of matrix representation looks something like this:
<div class="custom-image"><img src="https://66.media.tumblr.com/cac070475d2536589e76f47a67fecffd/tumblr_o7mwbbdvRl1rl36tko1_500.png" /></div>

###Round maze
While talking about the round maze, the situation changes. My intuition says that here polar geometry should be involved, which means we have to deal with r and theta.  
A good idea is creating the maze on the tree structure. <br />

The relation between our tree and the maze is as follows: <br />
<ul>
  <li>Each level (i) of the tree corresponds to a circle (i) in the maze, hence the number of circles in the maze equals the tree's height.</li>
  <li>A tree's node represents a door in a specific ring. For instance, the tree’s root is the entry point into the maze: a single gap in the outermost circle.</li>
  <li>Edges connecting node A at level (i) to node B at level (i+1) will ensure a direct path from ring (i) to an inner ring (i+1).</li>
  <li>A parent node P with two child nodes A and B (or more) will result in a barrier separating each child; this is because the only way of getting from a node in A’s sub-tree to any node in B’s sub-tree is by visiting P. </li>
  <li>A solution for the maze will be a path from the tree’s root to one of the nodes at the lowest level (a node with depth equals to the tree's height).</li>
</ul>

The full code project can be found on the <a href="https://github.com/dianaartiom/astar">Github repository</a> .


###Final touches:
A* is a very fast algorithm that uses heuristics to determine whether or not a path is viable. It is very useful for something such as path finding in computer games as there may be different routes available but some routes are preferable to others.

#Laboratory work Nr. 3

In this laboratory work we had to find the minimum for x ant y of a given function, in accordance to the following methods:
<ul>
  <li>
    Steepest descent method;
  </li>

  <li>
    Ant colony optimization algorithm.
  </li>
</ul>

The steepest descent method is an iterative function using the steepest descent.  To find the local minimum, you start at a random point, and move into the direction of steepest descent relative to the gradient, i.e. into the direction that goes down. First we need to choose a start point. Because we’re using gradient descent, we need to subtract the gradient from our x-coordinate. Also we need to multiply the gradient by a step size. This step size has to be chosen carefully, as a value too small will result in a long computation time, while a value too large will not give you the right result or even fail to converge.

The code(Written in Python):

```$
x1 = -3
y1 = -1

x2 = 3
y2 = 1

n = 0 # nr of iterations
value = 0.00000000001
step = 0.01

# Partial Derivatives
def partialWthRespectX(x, y):
    return 2/9*x*cos(x*x/9+y*y)

def partialWthRespectY(x, y):
    return 2*y*cos(y*y + x*x/9)


while abs(x2 - x1) and abs(y2 - y2):
    x1 = x2
    gradient = partialWthRespectX(x1, 0)
    move = gradient * step

    x2 = x1 - move
    y1 = y2
    gradient = partialWthRespectY(y1, 0)
    move = gradient * step
    y2 = y1 - move
    i += 1

print "Min for x: ", x1
print "Min for y: ", y1

```

### Ant colony optimization algorithm
According to official sources, Ant colony optimization (ACO) is a population-based metaheuristic that can be used to find approximate solutions to difficult optimization problems.

<br />

In ACO, a set of software agents called artificial ants search for good solutions to a given optimization problem. To apply ACO, the optimization problem is transformed into the problem of finding the best path on a weighted graph. The artificial ants (hereafter ants) incrementally build solutions by moving on the graph. The solution construction process is stochastic and is biased by a pheromone model, that is, a set of parameters associated with graph components (either nodes or edges) whose values are modified at runtime by the ants.

####Python code:

```
from math import *

xMin = 0
yMin = 0
init_x = 1.1
init_y = 0.8
alpha = 0.01
precision = 0.00000001

counter = 0

def f1(x, y):
    return 2 * x / 9 * cos((x * x / 9) + y * y)

def f2(x, y):
    return 2 * y * cos((x * x / 9) + y * y)

while(( abs( init_x - xMin)) > precision and (abs(init_y - yMin)) > precision) :
    if init_x >= 3 or init_x <= -3 or init_y >= 1 or init_y <= -1:
        continue
    counter += 1
    xMin = init_x
    init_x = xMin - alpha * f1(xMin, yMin)
    yMin = init_y
    init_y = yMin - alpha * f2(xMin, yMin)

print ("Iterations: ", counter)
print ("x min: ", init_x)
print ("y min: ", init_y)
```

##Conclusion:
As these algorithms are widely used in computer science, it is a great idea to apply these algorithms in practice. Only with a few lines of code, the efficiency can be increased.

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
