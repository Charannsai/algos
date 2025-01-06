
### UNIT I: Divide and Conquer

#### 1. Merge Sort

**Algorithm:**
MergeSort(A, low, high)  
1. If low < high, then:  
    - mid ← \(\lfloor (low + high)/2 \rfloor\)  
    - MergeSort(A, low, mid)  
    - MergeSort(A, mid + 1, high)  
    - Merge(A, low, mid, high)  

**Explanation:**  
- **Merge Sort** is a divide-and-conquer algorithm used to sort an array. It works by recursively dividing the array into two halves, sorting them, and then merging them back together in sorted order.  
- The **Merge** function merges two sorted subarrays into a single sorted array.  
- This process continues until the base case (array with a single element) is reached.

---

#### 2. Binary Search

**Algorithm:**
BinarySearch(A, low, high, key)  
1. If low > high:  
    - Return -1.  
2. mid ← \(\lfloor (low + high)/2 \rfloor\).  
3. If A[mid] == key:  
    - Return mid.  
4. Else if A[mid] > key:  
    - Return BinarySearch(A, low, mid-1, key).  
5. Else:  
    - Return BinarySearch(A, mid+1, high, key).  

**Explanation:**  
- **Binary Search** is a searching algorithm that works by repeatedly dividing the search interval in half. It is used on sorted arrays.  
- Starting with the middle element, if the key is equal to the middle element, the search ends.  
- If the key is smaller, the search continues in the left half; otherwise, it continues in the right half, repeating the process until the key is found or the search interval is empty.

---

#### 3. Strassen’s Matrix Multiplication

**Algorithm:**
Strassen(A, B)  
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

**Explanation:**  
- **Strassen’s Algorithm** is an optimized matrix multiplication algorithm that reduces the number of multiplications required.  
- Traditional matrix multiplication involves \(n^3\) multiplications, but Strassen’s algorithm reduces this to approximately \(n^{\log_2 7} \approx n^{2.81}\), making it faster for large matrices.  
- By dividing matrices into submatrices, Strassen computes 7 recursive multiplications instead of the usual 8 in standard matrix multiplication.

---

### UNIT II: Disjoint Sets and Backtracking

#### 4. Union-Find Algorithm

**Algorithm:**
UnionFind(n):  
1. Initialize parent array P[1..n] where P[i] = i.  
2. Define Find(x):  
    - While P[x] != x:  
        - x ← P[x].  
    - Return x.  
3. Define Union(x, y):  
    - P[Find(x)] ← Find(y).  
4. Return P.  

**Explanation:**  
- **Union-Find** is used to efficiently manage disjoint sets and is widely applied in algorithms like Kruskal’s for finding the Minimum Spanning Tree (MST).  
- The **Find** operation finds the root of the set containing element x, and the **Union** operation merges two sets into one.  
- The **parent array** stores the representative of each set, and the algorithm uses path compression to speed up future queries.

---

#### 5. N-Queens Problem (Backtracking)

**Algorithm:**
NQueens(n)  
1. Create an empty n × n board.  
2. Start placing queens one by one, checking if placing a queen violates any constraints (no two queens on the same row, column, or diagonal).  
3. If a queen can be placed without conflict, move to the next row and repeat the process.  
4. If all queens are placed, return the solution.  
5. If placing a queen leads to no solution, backtrack by removing the queen and trying another position.

**Explanation:**  
- The **N-Queens Problem** is a classic problem where the task is to place N queens on an N × N chessboard such that no two queens threaten each other.  
- Backtracking is used here, where the algorithm tries to place queens in valid positions, and if it encounters a conflict, it backtracks to try other positions.

---

#### 6. Hamiltonian Cycle (Backtracking)

**Algorithm:**
HamiltonianCycle(G, path, pos)  
1. If pos == n and G[path[pos-1]][path[0]] == 1:  
    - Return True.  
2. For v ← 1 to n:  
    - If v is not visited and G[path[pos-1]][v] == 1:  
        - path[pos] ← v.  
        - If HamiltonianCycle(G, path, pos+1):  
            - Return True.  
        - Backtrack.  
3. Return False.

**Explanation:**  
- The **Hamiltonian Cycle Problem** involves finding a cycle in a graph that visits every vertex exactly once and returns to the starting vertex.  
- Backtracking is used to explore possible paths, and if a cycle is found, the algorithm terminates. If no valid cycle is found, the algorithm backtracks and explores other possibilities.

---

### UNIT III: Dynamic Programming

#### 7. 0/1 Knapsack Problem

**Algorithm:**
Knapsack(W, wt[], val[], n)  
1. Create a table K[0..n][0..W].  
2. For i ← 0 to n:  
    - For w ← 0 to W:  
        - If i = 0 or w = 0:  
            - K[i][w] ← 0.  
        - Else if wt[i] ≤ w:  
            - K[i][w] ← max(val[i] + K[i-1][w-wt[i]], K[i-1][w]).  
        - Else:  
            - K[i][w] ← K[i-1][w].  
3. Return K[n][W].

**Explanation:**  
- The **0/1 Knapsack Problem** is a problem in which you have a set of items, each with a weight and a value, and you must select a subset of these items to maximize the total value while staying within a weight limit.  
- Dynamic programming is used to break the problem down into smaller subproblems, storing the results to avoid redundant calculations.

---

#### 8. Floyd-Warshall Algorithm (All Pairs Shortest Path)

**Algorithm:**
FloydWarshall(G)  
1. Let dist[1..n][1..n] ← G.  
2. For k ← 1 to n:  
    - For i ← 1 to n:  
        - For j ← 1 to n:  
            - dist[i][j] ← min(dist[i][j], dist[i][k] + dist[k][j]).  
3. Return dist.

**Explanation:**  
- **Floyd-Warshall** is a dynamic programming algorithm used to find the shortest paths between all pairs of vertices in a graph.  
- It iteratively updates the shortest path between pairs by considering intermediate vertices, leading to a time complexity of \(O(n^3)\).

---

### UNIT IV: Greedy Method

#### 9. Kruskal’s Algorithm (MST)

**Algorithm:**
Kruskal(G)  
1. Sort all edges of G in increasing order of weight.  
2. Initialize a set T to hold edges of the MST.  
3. For each edge (u, v) in sorted order:  
    - If u and v are in different connected components:  
        - Add (u, v) to T.  
4. Return T.

**Explanation:**  
- **Kruskal’s Algorithm** is used to find the Minimum Spanning Tree (MST) of a graph.  
- It works by sorting the edges by weight and adding them one by one to the MST, ensuring no cycles are formed by checking if the vertices are in different connected components.

---

#### 10. Job Scheduling with Deadlines

**Algorithm:**
JobScheduling(jobs)  
1. Sort jobs by decreasing profit.  
2. For each job:  
    - If a free slot exists before its deadline:  
        - Schedule the job.  
3. Return scheduled jobs and total profit.

**Explanation:**  
- **Job Scheduling** involves scheduling jobs with deadlines and profits such that the total profit is maximized.  
- The jobs are sorted by profit in descending order, and the algorithm attempts to schedule them in available slots before their deadlines.

---

### UNIT V: Branch and Bound

#### 11. Travelling Salesperson Problem (Branch and Bound)

**Algorithm:**
TSP_BnB(G)  
1. Initialize bound and priority queue.  
2. Enqueue root node.  
3. While queue is not empty:  
    - Dequeue a node.  
    - If promising, enqueue child nodes.  
4. Return shortest path.

**Explanation:**  
- **Branch and Bound** is a general algorithm for solving optimization problems like the Travelling Salesperson Problem (TSP).  
- The algorithm systematically explores all possible paths, but it "bounds" the search by discarding paths that cannot lead to an optimal solution.

---

#### 12. NP-Complete Verification

**Algorithm:**
Verify(Solution, Problem)  
1. If Solution satisfies Problem constraints:  
    - Return "Valid".  
2. Else:  
    - Return "Invalid".

**Explanation:**  
- **NP-Complete Verification** is used to check whether a given solution satisfies the constraints of an NP-complete problem.  
- The algorithm simply verifies whether the solution meets the problem’s conditions, returning "Valid" if it does and "Invalid" otherwise.

