# 2-D Dynamic Programming

2-D DP organizes states in tables keyed by two indices (row/column, i/j) to solve grid and string alignment problems.

## Problems

| Problem | Difficulty | Topics |
|---------|-----------|--------|
| Unique Paths | Medium | Dynamic Programming, Grid |
| Longest Common Subsequence | Medium | Dynamic Programming, String |
| Best Time to Buy And Sell Stock With Cooldown | Medium | Dynamic Programming, Stocks |
| Coin Change II | Medium | Dynamic Programming, Knapsack |
| Target Sum | Medium | Dynamic Programming, Subset Sum |
| Interleaving String | Medium | Dynamic Programming, String |
| Longest Increasing Path In a Matrix | Hard | Dynamic Programming, DFS |
| Distinct Subsequences | Hard | Dynamic Programming, String |
| Edit Distance | Medium | Dynamic Programming, String |
| Burst Balloons | Hard | Dynamic Programming, Interval |
| Regular Expression Matching | Hard | Dynamic Programming, String |

## Prerequisites

### 2-Dimension DP (Data Structures & Algorithms for Beginners)

Model states with two indices (rows/columns) and fill tables respecting dependencies.

### 0 / 1 Knapsack (Advanced Algorithms)

Turn selection problems into DP over capacity with include/exclude states.

### Unbounded Knapsack (Advanced Algorithms)

Handle unlimited copies of items by reusing states and iterating capacities accordingly.

### LCS (Advanced Algorithms)

Classic string DP that teaches overlap handling and diagonal transitions.

## Common Patterns

### Table Filling

Fill DP tables row by row or diagonally according to dependency order.

### State Compression

Whenever two rows suffice, reduce memory by keeping rolling arrays.
