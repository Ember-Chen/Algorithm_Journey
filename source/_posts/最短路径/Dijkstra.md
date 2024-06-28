---
title: Dijkstra
date: 2024-06-27
category: 最短路径
---
- 功能：求单个源点到所有其他节点的最短路径
<!--more-->
- T(N)=O(N^2^)
- Dijkstra有DP的思维在其中（每次加入1个元素，需要更新1次数据）
- Dijkstra和Prim是非常类似的
    - Dij每次更新的是`distance(遍历点, 出发点)`
        > 出发点始终固定
    - Prim更新的是`distance(遍历点, 当前结果集)`
        > 当前结果集每次更新大小增1

# 伪代码实现
```pseudocode
Dijkstra(Graph, source):
    V = number of vertices in Graph
    distance = array of size V, initialized to infinity
    distance[source] = 0

    priorityQueue = min-priority queue, initialized with (source, 0)

    while priorityQueue is not empty:
        u = priorityQueue.top.vertex
        priorityQueue.pop()
        for each neighbor v of u in Graph:
            weight = edge weight from u to v

            if distance[u] + weight < distance[v]:
                distance[v] = distance[u] + weight
                priorityQueue.insert((v, distance[v]))
        end for

    return distance
```


# cpp实现

```cpp
#include <vector>
#include <queue>
#include <utility>
using namespace std;
// 定义邻接表表示的图
typedef pair<int, int> Vertex; // first是目标顶点，second是权重
typedef vector<vector<Edge>> Graph;

void dijkstra(const Graph& graph, int source) {
    int V = graph.size();
    vector<int> distance(V, INT_MAX);
    distance[source] = 0;

    // 优先队列存储未处理的顶点及其当前已知的最短距离
    priority_queue<Vertex, vector<Vertex>, greater<Vertex>> pq;
    pq.push(make_pair(source, 0));

    while (!pq.empty()) { // 队列中存储可能的“中间节点”
        int u = pq.top().first; // 当前处理节点
        pq.pop();

        // 遍历与u相邻的顶点
        for (const Edge& edge : graph[u]) {
            int v = edge.first;
            int weight = edge.second;

            // 如果从u到v的路径更短，则更新距离
            if (distance[u] + weight < distance[v]) {
                distance[v] = distance[u] + weight;
                pq.push(make_pair(v, distance[v])); // 因为v节点被更新过，所以v可能重新作为中间节点
            }
        }
    }
}
```