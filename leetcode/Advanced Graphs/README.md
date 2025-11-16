# Advanced Graphs

Advanced graph problems combine shortest paths, spanning trees, and topological ordering to manage weighted or constrained graphs.

## Problems

| Problem | Difficulty | Topics |
|---------|-----------|--------|
| Network Delay Time | Medium | Graphs, Dijkstra |
| Reconstruct Itinerary | Hard | Graphs, Eulerian Path |
| Min Cost to Connect All Points | Medium | Graphs, MST |
| Swim In Rising Water | Hard | Graphs, Binary Search |
| Alien Dictionary | Hard | Graphs, Topological Sort |
| Cheapest Flights Within K Stops | Medium | Graphs, BFS |

## Prerequisites

### Dijkstra's (Advanced Algorithms)

Priority-queue based single-source shortest path for graphs with non-negative weights.

### Prim's (Advanced Algorithms)

Grow minimum spanning trees by attaching the cheapest edge that leaves the current tree.

### Kruskal's (Advanced Algorithms)

Sort edges and use union-find to form a minimum spanning tree greedily.

### Topological Sort (Advanced Algorithms)

Order DAG vertices so edges go from earlier to later nodes using Kahn's algorithm or DFS finishing times.

## Common Patterns

### Priority Queues

Use priority queues to extract the next best edge or node when weights matter.

### Graph Ordering

Topological sort or Eulerian paths establish valid visiting orders in directed graphs.
