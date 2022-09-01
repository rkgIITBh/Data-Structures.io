## Graph Properties and Computer Representation

Let us discuss some well known properties of an undirected graph before exploring the ways to process a
graph. 



<strong>Graph property-1</strong>: An undirected graph has even number of vertices of odd degrees.

The proof of the above property is simple. If we add the degrees of all vertices then 

<p style="text-align:center">
    &Sigma; deg[v] mod 2 = 0 (the sum is an even number, why?)
</p>

But summing of degrees of all even degree vertices gives an even number. It implies that the sum of 
degrees of all odd degree vertices must also be an even number. It implies that there can be only even
number of odd degree vertices.
      
<strong>Graph property-2</strong>: Let <i>G</i> be a graph with <i>n</i> vertices and assume that the
degree of each vertex is at least &#8968;<i>(n-1)/2</i>&#8969; then the graph is connected.

Let <i>n=2k</i>, for <i>k=1, 2, ...</i>. Let <i>G</i> be disjoint union of two complete subgraphs both having
<i>k</i> vertices. Then the degree of each vertex in <i>G</i> is at least <i>k-1</i>. However <i>G</i> is 
disconnected. So to have <i>G</i> connected the minimum vertex degree should be <i>k</i>. 

Now consider the case when <i>G</i> has <i>2k-1</i> vertices. Again let <i>G</i> be disjoint union of two 
complete subgraphs, one having <i>k</i> and other having <i>k-1</i> vertices. The minimum vertex degee 
required for this to be true is <i>k-2</i>. So, the minimum vertex degree required for <i>G</i> to be 
connected is <i>k-1</i>.

Combining the two cases the minimum vertex degree required for <i>G</i> to be connected is:

- <i>n/2</i> when <i>n</i> is even, and 
- <i>(n-1)/2</i> when <i>n</i> is odd. 

The two conditions for connectivity can be expressed together as &#8968;(n-1)/2&#8969;

<strong>Graph property-3</strong>: A connected graph with <i>n</i> vertices has at least
<i>n-1</i> edges.

Let <i>G</i> have 1 vertex. It is obviously connected. So, the property holds. Now let <i>G</i> be
a graph with <i>n &ge; 2</i> vertices. Choose an arbitrary vertex <i>v</i> from <i>G</i>. Consider
the subgraph <i>H = G - {v}</i>. <i>H</i> may consist of <i>k</i> connected components
<i>Z<sub>i</sub></i>. Assume that <i>Z<sub>i</sub></i> has <i>n<sub>i</sub></i> vertices. By 
the induction hypothesis each <i>Z<sub>i</sub></i> has at least <i>n<sub>i</sub>-1</i> edges. The 
total number of vertices in subgraphs is equal to

<p style="text-align:center">
    &Sigma;<sub>i</sub> (n<sub>i</sub>) = n-1  
</p>

We can continue the discussion on more graph properties. But our focus is graph algorithms. So we stop
the discussion on graph properties for the moment. Let us focus on the computer processing of graphs.
The first and foremost question is: how to represent a graph as abstract datatype?

A graph essentially represents relationships between objects or things. We can use a matrix to capture 
relationships between objects. Therefore, the standard form for computer representation of a graph with
<i>n</i> vertices is a matrix of size <i>n<sup>2</sup></i>. An entry 
<p style="text-align:center">
            <i>a[i, j] = 1</i> if there is edge <i>(i, j) &isin; E</i><br>
            <i>a[i, j] = 0</i> otherwise
            </p> 
In other words, the <i>ij</i>th entry is 1 if the object <i>i</i> is related to the object <i>j</i>. In
the pictorial representation, we denote the relationship by an edge joining the related objects. A 0 entry 
indicates the absence of an edge. The matrix is called the adjacency matrix because it represents the 
relationship if a vertex is adjacent to another. Figure 1 illustrates the adjacency matrix representation.
<p style="text-align:center">
   <img src="../images/adjacencyMatrix.png">
</p>
Processing a graph requires every entry of the adjacency matrix to be accessed. So any graph algorithm 
requires time of at least O(<i>n<sup>2</sup></i>). 

However, if the graph is sparse, then most entries of the adjacency matrix are zero. So, representing graphs
using a matrix is expensive. We can use a representation that lists the edges incident at every vertex. 
The adjacency list representation of a graph consists of <i>n</i> lists, one corresponding to each vertex.
Every edge is listed twice in such a representation. Adjacency list representation of the graph in 
Figure 1 is given below.
<p style="text-align:center">
   <img src="../images/adjacencyList.png">
</p>

[Back to Index](../index.md)
