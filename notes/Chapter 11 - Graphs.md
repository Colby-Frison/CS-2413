
# Graph definition 
- Graph = (Vertices, Edges)
- This is often how graphs are labeled in more concrete terms:
	- $G = (V,E)$
	- where $V = \{v_1, v_2, v_3, ...\}$ 
		- (V is a set of vertices/nodes)
	- and $E = \{e_1, e_2, e_3, ...\}$
		-  (E is a set of edges/links/arcs)

- Edges are the subset of the cartesian product of the vertexes.
- $E \subseteq V X V$
- $VXV$ is a graph where every vertex is is connected to every node including itself
	- This would be called a **complete graph**
- So $E$ is simply a graph that contains a subset of those edges

- The image below is a directed graph defined as $E = \{ `(1,2), (1,3), (3, 2), (3,4), (4,3) \}$
	- This says **1 goes to 2 and 1 goes to 3**, and **3 goes to 2 and 3 goes to 4** , and so on.
![[1200px-Directed_graph_no_background.svg.png]]

- In an undirected graph (3,4) is the same thing as (4,3), but as seen above both have to listed to show the nodes can be traversed in either direction
	- Along with that if we take (1,2) as an example, in this directed graph that only mean that 1 goes to 2, but in an **undirected graph** (1,2) would mean it can be traversed in either direction

- A **self loop** is an <u>edge that points to its own node</u>
	- so the edge would be $\{v_i, v_i\}$
	- An example of this can be seen in the acyclic graph below where node 'A' is pointing to its self 
	- Self loops apply to all types of graphs

- If a graph (directed or undirected) has <u>two edges between any two nodes</u>, these edges are called **parallel edges**
	- This can be seen in the example above between nodes 3 and 4.

- A **simple graph** is <u>a graph (directed or undirected) that does not have more than one edge between any two vertices (no parallel edges) and no edge starts and ends at the same vertex (no self-loops)</u>
	- So in the above example it is not simple because there are two edges connecting nodes 3 and 4
	- In the example below the undirected graph is simple, but the acyclic graph is not since there is a self loop

##  Graph types
Below are other types of graphs
![[Types-of-graphs.jpg]]

The degree of a node/vertex is its number of neighbors.
### weighted vs. unweighted graph
- Edges can also be complex objects
	- Each edge can have a numeric weight representing the "cost" of traversing that edge
- If the edges have a weight the graph is a **weighted graph**, if not it is **unweighted**
### Directed vs, undirected
- Edges can also contain directions
	- By default an undirected graph can be traversed ways
- In a directed graph an edge can only be traversed in one direction
	- In directed graphs edges can be thought of as a one way street
	- Graphs can also contain 2 edges for a given node pair indicating the nodes can be traversed in both directions, this can be seen in the image at the top of the document

- There are also mixed graphs which are graphs that are both directed and undirected, meaning some edges have a direction while other do not (meaning they can be traversed both ways) 
	- But this type is not covered so it can be disregarded

## Utilities
- Graphs can be very useful to develop an algorithm for efficient navigation
	- By making a directed weighted graph, the optimal route to go to any given place can be found very efficiently.
- Computer organization networks, so stuff like the internet can also be modeled using graphs
- In general there are a lot of optimization problems in computing that are solved using graphs
- Graphs can also be used to see how error resilient a network is to node and link failures
	- In other words it can help ensure if a node is broken pathways will not be cut off to the rest of the graph
	- This can be helpful in computer architecture, networking, and even with power grids

## Ways of Graph Storage
### Adjacency Matrix
- An adjacency matrix is a matrix of size $n^2$ ('n' being the number of nodes/vertices) used to represent a finite graph.
	- While this is a large space complexity, it allows for $O(n)$ time complexity to find any given element, so it is a pretty good trade off
- The elements of the matrix indicate whether a pair of vertices are adjacent or not in the graph
	- In unweighted this is done with ones or zeros (or a 2 if there is a self-loop as shown below). In weighted graphs however the weight of the edge can be used to mark the relationship.
	- This kind of represents a Boolean matrix as the values are either "on" or "off"
		- This isn't really true when it become more complex as self-loops and weights kinda break the Boolean rule

- In the special case of a finite simple graph the adjacency matrix is a [(0,1)-matrix](https://en.wikipedia.org/wiki/(0,1)-matrix "(0,1)-matrix") with zeros on its diagonal
	- This is almost seen below but the self-loop on 1 makes it non-simple

- If the graph is undirected (i.e. all the edges are bidirectional), the adjacency matrix is symmetric
	- As seen below
	- If the graph is directed its likely the adjacency matrix will not be symmetric  

Below is an example of an undirected non-simple graph with its adjacency matrix. The phrase "Coordinates are 1-6" simple is denoting the what the rows and columns belong to
![[Pasted image 20241205132141.png]]
#### Ways to store adjacency matrix
- **Row Major Ordering**: Stores matrix data row by row in memory.
- **Column Major Ordering**: Stores matrix data column by column in memory.
- **C++ Matrix**: Represents a matrix using a two-dimensional array in C++.
- **ArrayClass of ArrayClass Objects**: A matrix where each row is represented as an instance of `ArrayClass`.
- **Sparse Matrix Representation**: A matrix where most elements are zero, stored efficiently by only keeping track of non-zero elements.
	- This is probably the best method as a graph normally contains a lot of zeros, so the nature of a sparse matrix is quite beneficial
- **C++ Definitions**: Involves creating C++ classes or functions for each of these matrix representations.
### Adjacency List
- An adjacency list is simply a list of size n that contains linked lists, these linked lists point to the neighbors of that node.
![[Pasted image 20241205135944.png]]
- In comparison to adjacency matrix this structure is more beneficial when the neighbors of the node need to be found, but is significantly less efficient when a specific relation needs to be found
- It also requires less space than its matrix counterpart only having a $o(n + m)$ **space complexity**. This is because it only needs an array of size n and the amount of linked list nodes is proportional to the number of edges (m). 
	- In other words it doesn't need to store a bunch of 0s as the matrix does, but at the same time a matrix can be stored as a sparse list which takes out this downside, so it more or less comes down to what operations need to occur and not the space needed.

# Trees
- A tree is a **[connected](https://en.wikipedia.org/wiki/Connected_graph "Connected graph") [undirected graph](https://en.wikipedia.org/wiki/Undirected_graph "Undirected graph") with no [cycles](https://en.wikipedia.org/wiki/Cycle_(graph_theory) "Cycle (graph theory)").**
- It is a **spanning tree** of a graph _G_ if it spans _G_ (that is, it includes every vertex of _G_) and is a subgraph of _G_ (**every edge in the tree belongs to _G_**). 
	- $E' \subseteq E$ Where $E$ is the edges of the graph and $E'$ is the edges of the tree
- A spanning tree of a connected graph _G_ can also be defined as a maximal set of edges of _G_ that contains no cycle, or as a minimal set of edges that connect all vertices.
	- Since a spanning tree contains no cycles it is also the representation of a graph with the most edges possible without having a cycle

- A graph is a tree **if and only if** it does not contain a cycle.
- A connected graph with n vertices is a tree **if an only if** it has $n-1$ edges


## Fundamental cycles
<u>don't worry about this stuff just skip to searching section</u>
- Adding just one edge to a spanning tree will create a cycle; such a cycle is called a **fundamental cycle** with respect to that tree.
	- Since a spanning tree is the maximal representation without any cycle, any one added edge will create a cycle
	- Each cycle created by an added edge is distinct, so there is a one-to-one correspondence between **fundamental cycles and edges not in the spanning tree** 
- For a connected graph with $V$ vertices, any spanning tree will have $V-1$ edges($E'$)
- Thus, a graph of $E$ edges and one of its spanning trees will have $E - V + 1$ fundamental cycles (The number of edges $E$ subtracted by number of edges included in a spanning tree $E'$; giving the number of edges not included in the spanning tree). 
	- For any given spanning tree the set of all $E - V + 1$ fundamental cycles forms a [cycle basis](https://en.wikipedia.org/wiki/Cycle_basis "Cycle basis"), i.e., a basis for the [cycle space](https://en.wikipedia.org/wiki/Cycle_space "Cycle space").


## Fundamental cuts
- Dual to the notion of a fundamental cycle is the notion of a **fundamental cutset** with respect to a given spanning tree.
- By deleting just one edge of the spanning tree, the vertices are partitioned into two disjoint sets. 
	- Once again since spanning tree is max representation without cycles, the removal of one edge would result in a subset of nodes being disconnected from the rest of the tree
	- This results in the two distinct partitions(unique subsets of a set)
- The fundamental cutset is defined as the set of edges that must be removed from the graph _G_ to accomplish the same partition.
	- So although the fundamental cutset is in regards to a certain spanning tree the edges from the parent graph are also included
	- So this means the edges in the fundamental cutset will successfully partition the parent graph as well as the specific spanning tree
		- This does not guarantee a successful partition for other spanning trees as the other trees organize the graph in different ways so it is unknown if the partition will be correct
- Thus, each spanning tree defines a set of $V - 1$ fundamental cutsets, one for each edge of the spanning tree.
	- Once again going to the non-cyclic property of spanning tree when an edge is cut it will create a partition. Then the other edges are added to the set to also o the partition in the graph

## Cycles and cuts
- In short Fundamental cutset and cycles are linked
	- Edges in a **cycle** that aren't part of the spanning tree are related to the **cutsets** of the other edges in that cycle.
	- Similarly, edges in a **cutset** are found in cycles that involve the edge corresponding to that cutset.
- Think of a spanning tree as the "skeleton" of the graph. If you add an edge, it creates a loop (**fundamental cycle**). If you remove an edge from this skeleton, it breaks the tree into two parts (**fundamental cutset**). These two ideas are opposites, or **dual**, and matroids provide a mathematical way to formalize this relationship.
- In the simplest way possible the edges removed or added to form he cycle or cut will be found in the opposite operation
	- If an edge is cut that cut will be found in a cycle
	- If an edge is added it will be found in a cut

## Spanning forest
- A collection of disjoint (unconnected) trees is described as a _[forest](https://en.wikipedia.org/wiki/Forest_(graph_theory) "Forest (graph theory)")_.
- A **spanning forest** in a graph is a subgraph that is a forest with an additional requirement. There are two incompatible requirements in use, of which one is relatively rare, so I'm only gonna describe the common one.
	- A spanning forest is a forest that spans all of the vertices, meaning only that each vertex of the graph is a vertex in the forest
	- A connected graph may have a disconnected spanning forest, such as the forest with no edges, in which each vertex forms a single-vertex tree.

## Algorithms
### Construction
- A single spanning tree of a graph can be found in [linear time](https://en.wikipedia.org/wiki/Linear_time "Linear time")(o(n)) by either [depth-first search](https://en.wikipedia.org/wiki/Depth-first_search "Depth-first search") or [breadth-first search](https://en.wikipedia.org/wiki/Breadth-first_search "Breadth-first search").
	- More on those algorithms later
- In either case, one can form a spanning tree by connecting each vertex, other than the root vertex _v_, to the vertex from which it was discovered. This tree is known as a depth-first search tree or a breadth-first search tree according to the graph exploration algorithm used to construct it.
	- Depth-first search trees are a special case of a class of spanning trees called [Trémaux trees](https://en.wikipedia.org/wiki/Tr%C3%A9maux_tree "Trémaux tree"), named after the 19th-century discoverer of depth-first search.

For the next two sections see if their mentioned in the textbook if not just skip for now
### Optimization
### Randomization
### Enumeration
### In infinite graphs
### In directed  multigraphs


# Searching
## Depth first search (DFS)
### General
- **Depth-first search** (**DFS**) is an [algorithm](https://en.wikipedia.org/wiki/Algorithm "Algorithm") for traversing or searching [tree](https://en.wikipedia.org/wiki/Tree_data_structure "Tree data structure") or [graph](https://en.wikipedia.org/wiki/Graph_(data_structure) "Graph (data structure)") data structures. 
- The algorithm starts at the [root node](https://en.wikipedia.org/wiki/Tree_(data_structure)#Terminology "Tree (data structure)") (selecting some arbitrary node as the root node in the case of a graph) and explores as far as possible along each branch before backtracking. 

- Extra memory, usually a [stack](https://en.wikipedia.org/wiki/Stack_(abstract_data_type) "Stack (abstract data type)"), is needed to keep track of the nodes discovered so far along a specified branch which helps in backtracking of the graph.
### Properties
- The [time](https://en.wikipedia.org/wiki/Time_complexity "Time complexity") and [space](https://en.wikipedia.org/wiki/Memory_management "Memory management") analysis of DFS differs according to its application area, we'll be talking about DFS in the terms of computer science. 
- In theoretical computer science, DFS is typically used to traverse an **entire graph**, and takes time $O(|V| + |E|)$
	- $|V|$ is the number of [vertices](https://en.wikipedia.org/wiki/Vertex_(graph_theory) "Vertex (graph theory)") 
		- We normally denote 'n' as in number of nodes
	- $|E|$  the number of [edges](https://en.wikipedia.org/wiki/Edge_(graph_theory) "Edge (graph theory)"). 
		- We normally denote 'm' as in number of edges for space and time complexity
	- Using our standard notation it would be **$O(n + m)$
		- This is what was said in class so go off this
	- So DFS is linear in the size of the graph.
- In this applications it also uses space $O(|V|)$) in the worst case to store the [stack](https://en.wikipedia.org/wiki/Stack_(abstract_data_type) "Stack (abstract data type)") of vertices on the current search path as well as the set of already-visited vertices. 
	- 
	- Thus, in this setting, the time and space bounds are the same as for [breadth-first search](https://en.wikipedia.org/wiki/Breadth-first_search "Breadth-first search") and the choice of which of these two algorithms to use depends less on their complexity and more on the different properties of the vertex orderings the two algorithms produce.
### Pseudocode
- Here is the recursive implementation of DFS there is also a non-recursive implementation, but it is generally not as good (worse space complexity, and possibly duplicating vertices on the stack) 
![[Pasted image 20241205180751.png]]
(/\\/\\/\\/\\/\ convert this into actual text instead of picture and make more readable)

### How it was defined in lecture
- So the first step is to mark all of the nodes as not visited, this makes the DFS method slightly easier
``` c++
for(int i = 0, i < n ; i++){
	visited[i] = false; //marks node not visited
}
for (int i = 0; i < n; i++){
	if(!visited[i])
		DFS(i); // method call
}
```
- next up is the actual method
``` c++
DFS (vertex i) {
	visited[i] = true; // set the root to visited
	for each neighbor j of i
		if (!visited[j])
			DFS(j); // recursive call
}
```
- This version of DFS is not very efficient as it is using an array of size n to mark visited, its isnt a huge deal, but it isn't great
	-  This is how he did it though so do it like this
## Breadth first search (BFS)
[Breadth-first search](https://en.wikipedia.org/wiki/Breadth-first_search)
- in the simplest terms possible BFS is simply DFS  but with a queue instead of a stack, so instead of back tracking you simply go to the next node in the queue
- The way a graph is traversed by DFS is it goes to a certain node then adds all of its neighbors to a queue, then the next node in the queue is called. This sequence is continued until there is nothing left in the queue which indicates there are no more neighbors/the graph has been fully traversed

``` c++
BFS (vertex i){
	visited[i] = true;
	while(!Q.empty()){
		x<-Q.dequeue();
		for each neighbor j of x{
			if(!visited[j]){
				visited[j] = true;
				Q.enqueue[j];
			}
		}
	}
}
```
- As seen in the algorithm above it almost identical to the algorithm shown in DFS with a few difference
	- The most obvious being it is not a recursive function instead opting for a while loop, this is most likely to reserve the queue without having to pass the queue through recursion increasing space and time complexity
	- along with that it actually contains a queue data structure, this makes a slight change in order of operation
