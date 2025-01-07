### UNIT I: Divide and Conquer

#### Algorithm 1: Merge Sort

**MergeSort(A, low, high)**
1. If low < high then:
    - mid ← (floor (low + high)/2)
    - MergeSort(A, low, mid)
    - MergeSort(A, mid + 1, high)
    - Merge(A, low, mid, high)

**Merge(A, low, mid, high)**
1. Create temporary arrays L[1..mid-low+1] and R[1..high-mid].
2. Copy data from A[low..mid] into L and A[mid+1..high] into R.
3. Merge L and R back into A[low..high].
4. Return.

---

#### Algorithm 2: Binary Search

**BinarySearch(A, low, high, key)**
1. If low > high:
    - Return -1.
2. mid ← \(\lfloor (low + high)/2 \rfloor\).
3. If A[mid] == key:
    - Return mid.
4. Else if A[mid] > key:
    - Return BinarySearch(A, low, mid-1, key).
5. Else:
    - Return BinarySearch(A, mid+1, high, key).

---

#### Algorithm 3: Strassen’s Matrix Multiplication

**Strassen(A, B)**
1. Divide A and B into 4 submatrices each.
2. Compute 7 products:
    - M1 ← (A11 + A22)(B11 + B22)
    - M2 ← (A21 + A22)B11
    - M3 ← A11(B12 - B22)
    - M4 ← A22(B21 - B11)
    - M5 ← (A11 + A12)B22
    - M6 ← (A21 - A11)(B11 + B12)
    - M7 ← (A12 - A22)(B21 + B22)
3. Combine results to form C.
4. Return C.

---

### UNIT II: Disjoint Sets and Backtracking

#### Algorithm 4: Union-Find Algorithm

**UnionFind(n):**
1. Initialize parent array P[1..n] where P[i] = i.
2. Define Find(x):
    - While P[x] != x:
        - x ← P[x].
    - Return x.
3. Define Union(x, y):
    - P[Find(x)] ← Find(y).
4. Return P.

---

#### Algorithm 5: N-Queens Problem

Already provided as an example.

---

#### Algorithm 6: Hamiltonian Cycle (Backtracking)

**HamiltonianCycle(G, path, pos):**
1. If pos == n and G[path[pos-1]][path[0]] == 1:
    - Return True.
2. For v ← 1 to n:
    - If v is not visited and G[path[pos-1]][v] == 1:
        - path[pos] ← v.
        - If HamiltonianCycle(G, path, pos+1):
            - Return True.
        - Backtrack.
3. Return False.

---

### UNIT III: Dynamic Programming

#### Algorithm 7: 0/1 Knapsack Problem

**Knapsack(W, wt[], val[], n):**
1. Create a table K[0..n][0..W].
2. For i ← 0 to n:
    - For w ← 0 to W:
        - If i = 0 or w = 0:
            - K[i][w] ← 0.
        - Else if wt[i] <= w:
            - K[i][w] ← max(val[i] + K[i-1][w-wt[i]], K[i-1][w]).
        - Else:
            - K[i][w] ← K[i-1][w].
3. Return K[n][W].

---

#### Algorithm 8: All Pairs Shortest Path (Floyd-Warshall)

**FloydWarshall(G):**
1. Let dist[1..n][1..n] ← G.
2. For k ← 1 to n:
    - For i ← 1 to n:
        - For j ← 1 to n:
            - dist[i][j] ← min(dist[i][j], dist[i][k] + dist[k][j]).
3. Return dist.

---

### UNIT IV: Greedy Method

#### Algorithm 9: Kruskal’s Algorithm (MST)

**Kruskal(G):**
1. Sort all edges of G in increasing order of weight.
2. Initialize a set T to hold edges of the MST.
3. For each edge (u, v) in sorted order:
    - If u and v are in different connected components:
        - Add (u, v) to T.
4. Return T.

---

#### Algorithm 10: Job Scheduling with Deadlines

**JobScheduling(jobs):**
1. Sort jobs by decreasing profit.
2. For each job:
    - If a free slot exists before its deadline:
        - Schedule the job.
3. Return scheduled jobs and total profit.

---

### UNIT V: Branch and Bound

#### Algorithm 11: Travelling Salesperson Problem (Branch and Bound)

**TSP_BnB(G):**
1. Initialize bound and priority queue.
2. Enqueue root node.
3. While queue is not empty:
    - Dequeue a node.
    - If promising, enqueue child nodes.
4. Return shortest path.

---

#### Algorithm 12: NP-Complete Verification

**Verify(Solution, Problem):**
1. If Solution satisfies Problem constraints:
    - Return "Valid".
2. Else:
    - Return "Invalid".








---





 explanation of the differences between **Divide and Conquer**, **Backtracking**, **Dynamic Programming (DP)**, **Greedy**, and **Branch and Bound**, along with their use cases:


### 1. **Divide and Conquer**
- **Concept**: Break the problem into smaller subproblems, solve each subproblem independently, and combine their results to form the solution.
- **Key Idea**: Divide → Solve → Combine.
- **Use Case**: Problems where splitting makes it easier to solve independently.
- **Examples**:
  - **Merge Sort**: Split the array into halves, sort each half, and merge them.
  - **Binary Search**: Divide the array into two halves and search in the relevant half.

**When to Use**: Use when the problem can be naturally divided into independent parts.

---

### 2. **Backtracking**
- **Concept**: Explore all possible solutions recursively by trying one possibility at a time. If a solution doesn’t work, backtrack and try another.
- **Key Idea**: Try → Check → Backtrack.
- **Use Case**: Problems involving permutations, combinations, and constraints.
- **Examples**:
  - **Sudoku Solver**: Try filling each cell, and backtrack if a number violates the rules.
  - **N-Queens Problem**: Place queens on a chessboard such that no two threaten each other.

**When to Use**: Use when you need to explore multiple possibilities and constraints are involved.

---

### 3. **Dynamic Programming (DP)**
- **Concept**: Break the problem into overlapping subproblems, solve each once, and store the results to avoid redundant computation.
- **Key Idea**: Solve → Store → Reuse.
- **Use Case**: Optimization problems with overlapping subproblems and optimal substructure.
- **Examples**:
  - **Fibonacci Sequence**: Store results of previous calculations to avoid recalculating.
  - **Knapsack Problem**: Find the maximum value that can fit in a bag with weight constraints.

**When to Use**: Use when the problem has overlapping subproblems and requires optimization.

---

### 4. **Greedy**
- **Concept**: Make the locally optimal choice at each step, hoping to find the global optimum.
- **Key Idea**: Take → Move → Repeat.
- **Use Case**: Problems where a local decision leads to an overall optimal solution.
- **Examples**:
  - **Activity Selection**: Select the maximum number of non-overlapping activities.
  - **Huffman Encoding**: Build an optimal prefix code for data compression.

**When to Use**: Use when the problem exhibits the **greedy-choice property** (local choice leads to a global solution).

---

### 5. **Branch and Bound**
- **Concept**: Solve optimization problems by systematically exploring solution spaces, "bounding" to eliminate parts that cannot produce better solutions than the current best.
- **Key Idea**: Explore → Bound → Prune.
- **Use Case**: Optimization problems, especially NP-Hard ones.
- **Examples**:
  - **Traveling Salesman Problem (TSP)**: Find the shortest route visiting all cities.
  - **0/1 Knapsack**: Similar to DP but uses bounds to prune unnecessary calculations.

**When to Use**: Use when solving optimization problems where brute force is inefficient, and bounds can reduce search space.

---

### Quick Comparison Table:

| **Technique**     | **Key Idea**               | **Works Best For**                               | **Examples**                        |
|--------------------|---------------------------|--------------------------------------------------|--------------------------------------|
| **Divide & Conquer** | Divide → Solve → Combine  | Independent subproblems                          | Merge Sort, Binary Search            |
| **Backtracking**    | Try → Check → Backtrack   | Constraints and permutations                     | Sudoku Solver, N-Queens Problem      |
| **Dynamic Programming** | Solve → Store → Reuse    | Overlapping subproblems, optimization            | Fibonacci, Knapsack Problem          |
| **Greedy**          | Take → Move → Repeat      | Local choice leading to global solution          | Activity Selection, Huffman Encoding |
| **Branch & Bound**  | Explore → Bound → Prune   | Optimization with reduced search space           | TSP, 0/1 Knapsack Problem            |

---

### Summary:
- **Divide and Conquer** splits and combines subproblems.
- **Backtracking** tries all possible paths and undoes choices.
- **DP** stores previous results to optimize.
- **Greedy** makes local optimal choices.
- **Branch and Bound** uses bounds to cut off unnecessary paths in search.

Each technique is suited for specific types of problems, so understanding the problem structure helps in selecting the right approach.





Here is a breakdown of the topics in the syllabus with their respective time complexities for the relevant cases:

---

### **UNIT I**
#### **Divide and Conquer**
1. **Binary Search**  
   - Best Case: \(O(1)\)  
   - Average Case: \(O(\log n)\)  
   - Worst Case: \(O(\log n)\)
   
2. **Quick Sort**  
   - Best Case: \(O(n \log n)\)  
   - Average Case: \(O(n \log n)\)  
   - Worst Case: \(O(n^2)\)
   
3. **Merge Sort**  
   - Best Case: \(O(n \log n)\)  
   - Average Case: \(O(n \log n)\)  
   - Worst Case: \(O(n \log n)\)
   
4. **Strassen’s Matrix Multiplication**  
   - Best/Worst Case: \(O(n^{\log_2 7}) \approx O(n^{2.81})\)

---

### **UNIT II**
#### **Disjoint Sets**
1. **Union and Find Algorithms**  
   - Worst Case: \(O(\alpha(n))\), where \(\alpha\) is the Inverse Ackermann function (almost constant).

2. **Priority Queue (Heaps)**  
   - Insert: \(O(\log n)\)  
   - Delete/Extract-Min or Extract-Max: \(O(\log n)\)  
   - Build Heap: \(O(n)\)

#### **Backtracking**
1. **N-Queens Problem**  
   - Time Complexity: \(O(n!)\)

2. **Subset Sum Problem**  
   - Worst Case: \(O(2^n)\)

3. **Graph Coloring**  
   - Worst Case: \(O(k^n)\), where \(k\) is the number of colors.

4. **Hamiltonian Cycles**  
   - Worst Case: \(O(n!)\)

---

### **UNIT III**
#### **Dynamic Programming**
1. **Optimal Binary Search Tree**  
   - Time Complexity: \(O(n^3)\)

2. **0/1 Knapsack Problem**  
   - Time Complexity: \(O(n \times W)\), where \(W\) is the weight capacity.

3. **All-Pairs Shortest Path (Floyd-Warshall Algorithm)**  
   - Time Complexity: \(O(n^3)\)

4. **Traveling Salesperson Problem (TSP)**  
   - Time Complexity: \(O(n^2 \times 2^n)\)

5. **Reliability Design**  
   - Problem-specific but usually exponential in the worst case.

---

### **UNIT IV**
#### **Greedy Method**
1. **Job Sequencing with Deadlines**  
   - Time Complexity: \(O(n \log n)\)

2. **Knapsack Problem (Fractional)**  
   - Time Complexity: \(O(n \log n)\)

3. **Minimum Spanning Trees**  
   - Kruskal’s Algorithm: \(O(E \log V)\), where \(E\) is the number of edges and \(V\) is the number of vertices.  
   - Prim’s Algorithm: \(O(E + V \log V)\)

4. **Single-Source Shortest Path (Dijkstra’s Algorithm)**  
   - Time Complexity: \(O((V + E) \log V)\) using a priority queue.

#### **Traversal and Search Techniques**
1. **Binary Trees**  
   - Preorder/Inorder/Postorder Traversal: \(O(n)\)  

2. **Graphs (DFS/BFS)**  
   - Time Complexity: \(O(V + E)\)

3. **Connected Components**  
   - Time Complexity: \(O(V + E)\) (DFS/BFS-based)

---

### **UNIT V**
#### **Branch and Bound**
1. **Traveling Salesperson Problem (TSP)**  
   - Time Complexity: Exponential in the worst case (\(O(n!)\))  
   - Optimized via pruning.

2. **0/1 Knapsack Problem**  
   - Time Complexity: Exponential in the worst case (\(O(2^n)\)), depending on the number of branches.

3. **LC Branch and Bound vs. FIFO Branch and Bound**  
   - LC Branch: Prioritizes promising nodes; generally more efficient.  
   - FIFO Branch: Explores all nodes in BFS order; less efficient.

#### **NP-Hard and NP-Complete Problems**
1. **General Complexity**  
   - NP-Hard: Problems that are at least as hard as the hardest problems in NP.  
   - NP-Complete: Problems that are in NP and can be reduced to each other in polynomial time.  
   - Solving: Exponential in the worst case.
