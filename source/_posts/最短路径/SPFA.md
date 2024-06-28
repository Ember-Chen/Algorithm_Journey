---
title: SPFA
date: 2024-06-27
category: 最短路径
---
- 与Dijkstra的差异：使用pq还是que
- 与BellmanFord的差异：使用队列保存需要进行松弛的节点，避免了重复的计算

<!--more-->

```pseudocode
SPFA(Graph, source):
    V = number of vertices in Graph
    distance = array of size V, initialized to infinity
    inQueue = array of size V, initialized to false
    distance[source] = 0

    queue = empty queue
    queue.enqueue(source)
    inQueue[source] = true

    while queue is not empty:
        u = queue.dequeue()
        inQueue[u] = false

        for each neighbor v of u in Graph:
            weight = edge weight from u to v

            if distance[u] + weight < distance[v]:
                distance[v] = distance[u] + weight

                if not inQueue[v]:
                    queue.enqueue(v)
                    inQueue[v] = true

    return distance
```