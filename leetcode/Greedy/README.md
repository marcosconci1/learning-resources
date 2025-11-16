# Greedy

Greedy solutions make the locally optimal choice each step and prove that it leads to a global optimum.

## Problems

| Problem | Difficulty | Topics |
|---------|-----------|--------|
| Maximum Subarray | Medium | Greedy, Kadane |
| Jump Game | Medium | Greedy, Array |
| Jump Game II | Medium | Greedy, BFS |
| Gas Station | Medium | Greedy, Circular |
| Hand of Straights | Medium | Greedy, Hash Map |
| Merge Triplets to Form Target Triplet | Medium | Greedy, Array |
| Partition Labels | Medium | Greedy, String |
| Valid Parenthesis String | Medium | Greedy, Counting |

## Prerequisites

### Kadane's Algorithm (Advanced Algorithms)

Linear-time trick to track the best subarray sum using running totals and resets.

## Common Patterns

### Running Best

Track the best seen so far and reset when the running score drops below zero.

### Reach Tracking

Maintain the farthest reachable index while iterating once for jump-style problems.
