---
title: BellmanFord
date: 2024-06-27
category: 最短路径
---
- BellmanFord vs. Floyd-Warshall
    - BellmanFord：解决的是单源点到剩余其他所有节点的最短路长度
    - FloydWarshall：解决的是任意2点间的最短路长度

<!--more-->

```cpp
#include <vector>
using namespace std;
struct Edge {
    int source, target, weight;
};

// 判断全局起点能否到达vertex
bool unreachable(int vertex, vector<int>& distance){
    return distance[vertex]==INT_MAX;
}

void bellmanFord(int source, const vector<Edge>& edges, int V) {
    vector<int> distance(V, INT_MAX); // distance[i]：<source,t>的最短路长度
    distance[source] = 0; // 初始化

    for (int i = 0; i < V - 1; i+=1) { // 固定循环V-1次relax
        for (const Edge& edge : edges) {
            /**
            对于这一条边，如果全局起点source能够到达这条边的source，则判断“新距离能否刷新当前保存的最短距离”
             */
            if (!unreachable(edge.source)) {
                int newDistance = distance[edge.source] + edge.weight;
                distance[edge.target] = max(distance[edge.target],newDistance);
            }
        }
    }
}
```

