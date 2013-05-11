---
layout: post
title: "notes for algorithm"
description: ""
category: 
tags: []
---
{% include JB/setup %}

algorithm for connected component:

# Depth-First Search (DFS) #

Use `stack`




# Breadth-first Search (BFS) #

Use `Queue`


1. Enqueue the root node
2. Dequeue a node and examine it
- If the element sought is found in this node, quit the search and return a result.
- Otherwise enqueue any successors (the direct child nodes) that have not yet been discovered.
3. If the queue is empty, every node on the graph has been examined – quit the search and return "not found".
4. If the queue is not empty, repeat from Step 2.


Pseudocode:

	1  procedure BFS(G,v):
	2      create a queue Q
	3      enqueue v onto Q
	4      mark v
	5      while Q is not empty:
	6          t ← Q.dequeue()
	7          if t is what we are looking for:
	8              return t
	9          for all edges e in G.adjacentEdges(t) do
	12             u ← G.adjacentVertex(t,e)
	13             if u is not marked:
	14                  mark u
	15                  enqueue u onto Q
	16     return none
