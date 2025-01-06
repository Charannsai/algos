Here is a list of algorithms written in the same style and format as the handwritten N-Queens example you provided. Each algorithm is tailored for ease of understanding and directly relates to the syllabus topics provided.

---

### UNIT I: Divide and Conquer

#### Algorithm 1: Merge Sort

**MergeSort(A, low, high)**
1. If low < high then:
    - mid ← \(\lfloor (low + high)/2 \rfloor\)
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

This comprehensive list covers all the major topics and algorithms specified in the syllabus. Let me know if you need additional explanations or implementations for any specific algorithm!

