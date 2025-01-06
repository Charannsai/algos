
---

### **Algorithm 1: Merge Sort**

**MergeSort(A, low, high)**
1. If low < high:
   - Calculate mid = (low + high) // 2
   - Call MergeSort(A, low, mid)
   - Call MergeSort(A, mid + 1, high)
   - Merge(A, low, mid, high)

**Merge(A, low, mid, high)**
1. Create temporary arrays L = A[low...mid], R = A[mid+1...high]
2. Merge L and R back into A[low...high] by comparing elements
3. Copy any remaining elements of L and R, if present

**Explanation:**
Merge Sort works by using the divide-and-conquer strategy:
1. **Divide:** The array is split into halves recursively until subarrays of size 1 are achieved.
2. **Conquer:** The subarrays are sorted by merging them in sorted order. During merging, elements from the two halves are compared, and the smaller element is placed first.
3. **Combine:** The two sorted subarrays are merged into a single sorted array.
   
This recursive approach ensures that all subarrays are sorted, and the time complexity is \( O(n \log n) \).

---

### **Algorithm 2: Quick Sort**

**QuickSort(A, low, high)**
1. If low < high:
   - PartitionIndex = Partition(A, low, high)
   - Call QuickSort(A, low, PartitionIndex - 1)
   - Call QuickSort(A, PartitionIndex + 1, high)

**Partition(A, low, high)**
1. Choose pivot = A[high]
2. Initialize i = low - 1
3. For j = low to high - 1:
   - If A[j] <= pivot:
     - Increment i
     - Swap A[i] and A[j]
4. Swap A[i + 1] and A[high]
5. Return i + 1

**Explanation:**
Quick Sort is a comparison-based sorting algorithm that works by selecting a pivot element and partitioning the array into two subarrays: elements less than the pivot and elements greater than the pivot.
1. **Partition:** Select a pivot and reorder the array such that smaller elements come before the pivot, and larger ones come after. The pivot is then placed in its correct sorted position.
2. **Recursive Sort:** Recursively apply the same procedure to the left and right subarrays.

Quick Sort is efficient for large datasets with an average time complexity of \( O(n \log n) \), though in the worst case it can degrade to \( O(n^2) \) if the pivot selection is poor.

---

### **Algorithm 3: Strassen’s Matrix Multiplication**

**Strassen(A, B)**
1. Divide matrices A and B into four submatrices of size \( n/2 \times n/2 \).
2. Compute seven products using Strassen's formulas:
   - P1 = (A11 + A22)(B11 + B22)
   - P2 = (A21 + A22)B11
   - P3 = A11(B12 - B22)
   - P4 = A22(B21 - B11)
   - P5 = (A11 + A12)B22
   - P6 = (A21 - A11)(B11 + B12)
   - P7 = (A12 - A22)(B21 + B22)
3. Combine the results to form the product matrix C.

**Explanation:**
Strassen’s matrix multiplication algorithm improves on the classical matrix multiplication approach:
1. **Divide:** The matrices are recursively divided into smaller submatrices.
2. **Conquer:** Seven specific products are computed for the submatrices, reducing the number of multiplications from 8 to 7.
3. **Combine:** The results are combined to compute the final product.

This reduces the time complexity of matrix multiplication from \( O(n^3) \) to approximately \( O(n^{2.81}) \), making it faster for large matrices.

---

### **Algorithm 4: Union-Find Algorithm**

**UnionFind(n):**
1. Initialize parent array Parent[] and rank array Rank[]:
   - Parent[i] = i for i in range(1, n + 1)
   - Rank[i] = 0

**Find(x):**
1. If Parent[x] != x:
   - Parent[x] = Find(Parent[x])
2. Return Parent[x]

**Union(x, y):**
1. RootX = Find(x)
2. RootY = Find(y)
3. If RootX != RootY:
   - If Rank[RootX] > Rank[RootY]:
     - Parent[RootY] = RootX
   - Else If Rank[RootX] < Rank[RootY]:
     - Parent[RootX] = RootY
   - Else:
     - Parent[RootY] = RootX
     - Rank[RootX] += 1

**Explanation:**
Union-Find is used to efficiently manage disjoint sets and detect cycles in graphs.
1. **Find:** The `Find` operation retrieves the root of the set containing element \( x \), with path compression to optimize future queries.
2. **Union:** The `Union` operation combines two sets by linking their roots. It uses union by rank to keep the tree shallow.

The algorithm is nearly constant time, with a time complexity of \( O(\alpha(n)) \), where \( \alpha \) is the inverse Ackermann function, which grows very slowly.

---

### **Algorithm 5: N-Queens Problem**

**NQueens(k, n):**
1. For i = 1 to n:
   - If Place(k, i):
     - X[k] = i
     - If k == n:
       - Print solution X[1...n]
     - Else:
       - NQueens(k + 1, n)

**Place(k, i):**
1. For j = 1 to k - 1:
   - If X[j] == i or abs(X[j] - i) == abs(j - k):
     - Return False
2. Return True

**Explanation:**
The N-Queens problem uses backtracking to place \( n \) queens on an \( n \times n \) chessboard such that no two queens can attack each other.
1. **Place:** The `Place` function checks if placing a queen in a given position is valid by ensuring no two queens are in the same column or diagonal.
2. **Backtracking:** The algorithm recursively tries to place queens in each row and backtracks if a solution is not possible.

The problem has a time complexity of \( O(n!) \), as there are \( n! \) possible placements to check.

---

### **Algorithm 6: 0/1 Knapsack Problem**

**Knapsack(W, wt[], val[], n):**
1. Initialize dp array dp[n + 1][W + 1]
2. For i = 0 to n:
   - For w = 0 to W:
     - If i == 0 or w == 0:
       - dp[i][w] = 0
     - Else If wt[i - 1] <= w:
       - dp[i][w] = max(val[i - 1] + dp[i - 1][w - wt[i - 1]], dp[i - 1][w])
     - Else:
       - dp[i][w] = dp[i - 1][w]
3. Return dp[n][W]

**Explanation:**
The 0/1 Knapsack problem uses dynamic programming to solve the problem of selecting items to maximize value without exceeding the weight capacity.
1. **Dynamic Programming Table:** A table is built where `dp[i][w]` represents the maximum value that can be obtained using the first \( i \) items with a weight limit of \( w \).
2. **Iterative Computation:** Each item is considered, and for each weight capacity, the algorithm decides whether to include or exclude the item.
   
The time complexity is \( O(nW) \), where \( n \) is the number of items and \( W \) is the knapsack capacity.

---

### **Algorithm 7: Kruskal’s Algorithm (MST)**

**Kruskal(G):**
1. Sort edges of G by weight
2. Initialize empty set MST and use Union-Find for connected components
3. For each edge (u, v) in sorted edges:
   - If Find(u) != Find(v):
     - Add (u, v) to MST
     - Union(u, v)
4. Return MST

**Explanation:**
Kruskal’s algorithm constructs a Minimum Spanning Tree (MST) by:
1. **Sorting:** Sorting all edges by weight.
2. **Union-Find:** Using Union-Find to keep track of connected components and prevent cycles.
3. **Adding Edges:** Adding edges to the MST that do not form cycles, ensuring that the total weight is minimized.

The time complexity is \( O(E \log E) \), where \( E \) is the number of edges.

---

### **Algorithm 8: Travelling Salesperson Problem (Branch and Bound)**

**TSP_BnB(G):**
1. Initialize priority queue with root node (starting city)
2. While queue is not empty:
   - Dequeue node with minimum bound
   - If node is a leaf and completes a tour:
     - Update best solution if it’s better
   - Else:
     - Generate child nodes by visiting unvisited cities
     - Calculate bounds for child nodes and enqueue if bound < current best

**Explanation:**
The Traveling Salesperson Problem (TSP) seeks the shortest route to visit all cities exactly once. Using the Branch and Bound method:
1. **Bound Calculation:** A lower bound for the length of the tour is calculated at each step to prune paths that are unlikely to provide better solutions.
2. **Exploration:** The algorithm explores the search tree using a priority queue and prunes branches that cannot lead to better solutions.
   
TSP's worst-case complexity is exponential, with time complexity \( O(n!) \).

---
