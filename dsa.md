# DSA Master Roadmap (Based on 2026 Cheatsheet)

## 1. Complexity Analysis
* Time Complexity (Big-O):
  * Constant: O(1)
  * Logarithmic: O(log n)
  * Linear: O(n)
  * Linearithmic: O(n log n)
  * Quadratic: O(n^2)
  * Exponential: O(2^n)
  * Factorial: O(n!)
* Space Complexity: Evaluated similarly to time complexity to measure extra memory usage.

## 2. Data Structures
* Linear: Array, Linked List, Stack (LIFO), Queue (FIFO), Deque, String
* Non-Linear: Tree, Binary Tree, BST (Binary Search Tree), Heap (Min/Max), Graph, Hash Table

## 3. Algorithms
* Sorting:
  * Bubble Sort: O(n^2)
  * Selection Sort: O(n^2)
  * Insertion Sort: O(n^2)
  * Merge Sort: O(n log n)
  * Quick Sort: O(n log n)
  * Heap Sort: O(n log n)
  * Counting Sort: O(n+k)
  * Radix Sort: O(nk)
* Searching:
  * Linear Search: O(n)
  * Binary Search: O(log n)

## 4. Common Patterns
* Two Pointers
* Sliding Window
* Fast & Slow Pointer
* Merge Intervals
* Cyclic Sort
* Top K Elements
* Backtracking
* Divide & Conquer
* Greedy
* Dynamic Programming
* BFS / DFS

## 5. Array / String
* Traversal
* Insertion / Deletion
* Prefix Sum
* Two Pointers
* Kadane's Algorithm (Max Subarray Sum)

## 6. Linked List
* Traversal
* Insertion / Deletion
* Reverse a List
* Detect Cycle (Floyd’s algorithm)
* Merge Two Lists

## 7. Stack & Queue
* Stack (LIFO) operations: push(), pop(), peek()/top(), isEmpty()
* Queue (FIFO) operations: enqueue(), dequeue(), front(), isEmpty()

## 8. Trees
* Traversals: Inorder (LNR), Preorder (NLR), Postorder (LRN), Level Order (BFS)
* Height / Depth
* Diameter
* Check BST
* LCA (Lowest Common Ancestor)

## 9. Graphs
* Representations: Adjacency List, Adjacency Matrix
* Traversals: BFS, DFS
* Shortest Path: Dijkstra (Weighted), Bellman Ford
* MST: Kruskal, Prim
* Topological Sort (DAG)

## 10. Heap (Min/Max)
* Complete Binary Tree
* Min-Heap (parent <= child), Max-Heap (parent >= child)
* Operations: insert() O(log n), extractMin/Max() O(log n), peek() O(1)

## 11. Hash Table
* Key-Value mapping with average O(1) operations (insert, get, delete, contains)
* Use Cases: Counting, Caching, Frequency Map, Two Sum

## 12. Dynamic Programming
* Steps:
  1. Define State
  2. Write Recurrence
  3. Choose Order
  4. Add Memoization / Tabulation
* Common Problems: Fibonacci, Knapsack (0/1), LCS, Coin Change, Matrix Chain Multiplication

## 13. Important Formulas
* Sum of first n numbers: n(n+1) / 2
* Sum of squares: n(n+1)(2n+1) / 6
* Combinations (nCr): n! / (r!(n-r)!)
* Log rules: log(xy) = log x + log y, log(x/y) = log x - log y

## 14. Bit Manipulation
* Operators: AND (&), OR (|), XOR (^), NOT (~), Left Shift (<<), Right Shift (>>)
* Operations: Check bit, Set bit, Toggle bit, Invert bits

## 15. Golden Rules & Discipline
* Understand -> Dry Run -> Code -> Test -> Optimize -> Repeat
* Daily Mantra: Practice LeetCode Daily, stay consistent, and remember: Discipline today means success tomorrow.
