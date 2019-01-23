---
title: Go Algorithms
tags: [Notebooks/Cmput 496]
---

**[Go Algorithms](https://webdocs.cs.ualberta.ca/~mmueller/courses/496-current/slides/lecture1.pdf)**

### Capturing Stones Algorithm
  ![Capturing Algorithms](@attachment/cmput496/capture_algorithms.png)
  1. Look at all neighbors nb of p which are stones of opponent
  2. Check if block of nb loses its last liberty
  3. Similar to floodfill in graphics, or depth-first search in graph
  4. Look at all stones connected to nb
  5. If any stone has a liberty(other than p),stop:no capture
  6. If no stone in the block has another liberty, then all are capturedall neighbors

### Floodfill Algorithms
  1. Keep track of points already visited
  2. Visit all neighbors
  3. If they are the right color, then recursively visit their neighbors
  4. Depth-first search
  5. Different ways to implement
    * explicit recursion
    * Store points to be processed in a stack
  6. Resources page has some references for your review
  
###
