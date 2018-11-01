+++
title = "Introduction"
weight = 1
+++

```python
# Given a adj graph
graph = {1: [2,3], 2:[3]}

def topsort(graph):
    stack, seen = [], set()

    for g in graph:
        dfs(g, seen, graph, stack)
    return stack[::-1]

def dfs(g, seen, graph, stack):
    if g in seen:
        return
    
    seen.add(g)

    for c in graph[g]:
        dfs(c, seen, graph, stack)
    
    stack.append(g)

```