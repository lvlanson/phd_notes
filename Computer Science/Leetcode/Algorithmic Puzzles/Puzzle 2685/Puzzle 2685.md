---
type: [Disjoint-Set Union]
---
You are given an integer `n`. There is an **undirected** graph with `n` vertices, numbered from `0` to `n - 1`. You are given a 2D integer array `edges` where `edges[i] = [a_i, b_i]` denotes that there exists an **undirected** edge connecting vertices `a_i` and `b_i`.

Return *the number of **complete connected components** of the graph*.

A **connected component** is a subgraph of a graph in which there exists a path between any two vertices, and no vertex of the subgraph shares an edge with a vertex outside the subgraph.

A connected component is said to be **complete** if there exists an edge between every pair of its vertices.

**Example 1:**

![[screenshot-from-2023-04-11-23-31-23.png | center]]
```
Input: n = 6, edges = [[0,1],[0,2],[1,2],[3,4]]
Output: 3
```
**Explanation:** From the picture above, one can see that all of the components of this graph are complete.

**Example 2:**

![[screenshot-from-2023-04-11-23-32-00.png| center]]
```
Input: n = 6, edges = [[0,1],[0,2],[1,2],[3,4],[3,5]]
Output: 1
```
**Explanation:** The component containing vertices 0, 1, and 2 is complete since there is an edge between every pair of two vertices. On the other hand, the component containing vertices 3, 4, and 5 is not complete since there is no edge between vertices 4 and 5. Thus, the number of complete components in this graph is 1.

**Constraints:**

- `1 <= n <= 50`
- `0 <= edges.length <= n * (n - 1) / 2`
- `edges[i].length == 2`
- `0 <= a_i, b_i <= n - 1`
- `a_i != b_i`
- There are no repeated edges.

---

## **<span style="color:#38ffa9">Theory</span>**

Note, we want to find all subgraphs, therefore we will use the **disjoint-set union**

Lets take example 1, we have
```
Input: n = 6, edges = [[0,1],[0,2],[1,2],[3,4]]
```
To create the *disjoint-set data structure*, we have to use the following functions
>1. **Make-Set(x):** Create for each node `x` a set 
>2. **Union(x, y):** If two nodes `x,y` are connected by an edge but not in the same set, unite the sets they are located in
>3. **FInd-Set(x):** Find the set, which contains node `x`, and return some identification of the set

Let's play this out on the example, first we create a set for each node from `0` to `5` (`n=5`). We get
$$\Big\{ \{ i \} \Big\}_{i=0}^5 = \Big\{ \{ 0 \}, \{ 1 \}, \{ 2 \},\{ 3 \},\{ 4 \}, \{  5 \} \Big\}$$
Now we iterate over the edges, we have
$$\begin{align}
e_{0} &= (0,1) \implies \Big\{ \{ 0 , 1 \}, \{ 2 \},\{ 3 \},\{ 4 \}, \{  5 \} \Big\} \\ 
e_{1} &= (0,2) \implies \Big\{ \{ 0 , 1, 2 \},\{ 3 \},\{ 4 \}, \{  5 \} \Big\}  \\
e_{2} &= (1,2) \implies \Big\{ \{ 0 , 1, 2 \},\{ 3 \},\{ 4 \}, \{  5 \} \Big\} \\
e_{3} &= (3,4) \implies \Big\{ \{ 0 , 1, 2 \},\{ 3, 4 \}, \{  5 \} \Big\}
\end{align}$$
Now we have found all subgraphs.

## **<span style="color:#38ffa9">Strategy</span>**

We will create the **<span style="color:#38ffa9">disjoint-set union</span>**. In this task we want to count all **<span style="color:#38ffa9">complete subgraphs</span>**, i.e. where all nodes are connected to each other. Note, that in a **<span style="color:#38ffa9">complete subgraph</span>** of order $n$ each node has $n-1$ edges. Hence, we will count all edges for each node while creating the *disjoint-set union*.
<!--
```pseudo
\begin{algorithm}
\caption{countCompleteComponents}
\begin{algorithmic}
\Input $n$: Number of Nodes, $edges$: Set of Tuples \\
subGraphs := $\Big\{\{i\}\Big\}_{i=0}^{n-1} = \Big\{ \{ 0 \}, \{ 1 \}, \ldots, \{  n-1 \} \Big\}$  \\
edgeCount := $(0)_{i=1}^n \subset \mathbb{N}^n$ \\
encoding := $(i)_{i=0}^{n-1}$ (encodes which node is in which subgraph)\\
\ForAll{$(v_1,v_2) \leftarrow edges$}
	\State edgeCount[$v_1$]++
	\State edgeCount[$v_2$]++
	\If{Find-Set($v_1$) $\neq$ Find-Set($v_2$)}
		\State Union(subGraphs, $v_1, v_2$)
		\State Update(encoding, $v_1$, $v_2$)
    \EndIf
\EndFor

\State counter := 0
\ForAll{graph $\leftarrow$ subGraphs}
	\State vertexCount := countNodes(graph)
	\If{$\forall v \in$ graph: edgeCount[v] = vertexCount $- 1$}
		\State counter++		
    \EndIf

	
\EndFor
\Output counter
\end{algorithmic}
\end{algorithm}
```
-->
![[Pasted image 20250322192223.png]]
Note, the `Find-Set`method is just a lookup in the `encoding` array, and the update function handles the logic of keeping the encoding up-to-date dependent on the used data-structure.

## **<span style="color:#38ffa9">Implementation</span>**

My personal go implementation looks as follows

```go showLineNumbers
func countCompleteComponents(n int, edges [][]int) int {
    sets := make([][]int, n, n)
    setPos  := make([]int, n, n)
    edgeArr := make([]int, n, n)
    for i := 0; i < n; i++{
        sets[i] = append(sets[i], i)
        setPos[i] = i
    }

    for _, e := range edges{
        indexU := setPos[e[0]]
        indexV := setPos[e[1]]
        edgeArr[e[0]]++
        edgeArr[e[1]]++
        // merge
        if indexU != indexV{
            for _, item := range sets[indexV]{
                setPos[item] = indexU
            }
            sets[indexU] = append(sets[indexU], sets[indexV]...)
            sets[indexV] = []int{}
        }
    }
    counter := 0
    for _, set := range sets{
        if len(set) == 0{
            continue
        }
        isValid := true
        for _, el := range set{
            if edgeArr[el] != len(set) - 1{
                isValid = false
            }
        }
        if isValid{
            counter++
        }
    }
    return counter
}
```