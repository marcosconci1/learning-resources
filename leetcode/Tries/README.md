# Tries

Tries store prefixes explicitly, making them perfect for dictionary operations and prefix-aware searches.

## Problems

| Problem | Difficulty | Topics |
|---------|-----------|--------|
| Implement Trie Prefix Tree | Medium | Trie, Design |
| Design Add And Search Words Data Structure | Medium | Trie, Backtracking |
| Word Search II | Hard | Trie, Backtracking |

## Prerequisites

### Trie (Advanced Algorithms)

Prefix trees that store characters in layers so that insert/search share common prefixes efficiently.

## Common Patterns

### Prefix Storage

Create nodes per character and mark word endings to build dictionary-like structures.

### Trie + DFS

Combine trie traversal with DFS on a board or word to prune searches early.
