# Sliding Window

Sliding window strategies maintain a subarray or substring by expanding and contracting two indices, frequently achieving linear time solutions.

## Problems

| Problem | Difficulty | Topics |
|---------|-----------|--------|
| Best Time to Buy And Sell Stock | Easy | Sliding Window, Array |
| Longest Substring Without Repeating Characters | Medium | Sliding Window, Hash Map |
| Longest Repeating Character Replacement | Medium | Sliding Window, Frequency Counter |
| Permutation In String | Medium | Sliding Window, Frequency Counter |
| Minimum Window Substring | Hard | Sliding Window, Hash Map |
| Sliding Window Maximum | Hard | Sliding Window, Monotonic Queue |

## Prerequisites

### Sliding Window Fixed Size (Advanced Algorithms)

Use two indices to keep a window of a strict length while updating aggregates in O(1) per move.

### Sliding Window Variable Size (Advanced Algorithms)

Grow and shrink windows dynamically as constraints change to produce optimal subarrays in linear time.

## Common Patterns

### Fixed Window

Keep window length constant and update aggregates as the right pointer advances.

### Variable Window

Expand while constraints hold and shrink when they break to maintain optimal subarrays.
