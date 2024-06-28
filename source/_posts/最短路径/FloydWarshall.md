---
title: FloydWarshall
date: 2024-06-27
category: 最短路径
---

- 又称为插点法，是一种利用动态规划的思想寻找给定的加权图中多源点之间最短路径的算法，与Dijkstra算法类似
- 时间复杂度O(n^3^)

<!--more-->
```pseudocode
遍历所有节点，分别选择节点作为中间节点k{
    遍历所有节点，分别选择节点作为起点i{
        遍历所有节点，分别选择节点作为终点j{
            1.计算得到原来的i->j的路径长度
            2.计算得到i->k->j的路径长度
            3.更新i->j的路径长度为 二者的较小值
        }
    }
}
```

```cpp
int[][] graph;
const INF = MAX_INT;
int getNewLen(int start, int mid, int end){
    int lenA = graph[start][mid];
    int lenB = graph[mid][end];
    if(lenA==INF || lenB==INF)
        return INF;
    return lenA+lenB;
} // 潜在风险：溢出

void floyd(){
    for(int k=0; k<graph.length; k+=1){ // k: 加入路径的中间节点
        for(int i=0; i<gpaph.length; i+=1){ // i: 路径起点
            for(int j=0; j<graph.length){ // j: 路径终点
                // 分析i->j路径，与其和i->k>j路径比较
                int oldLen = graph[i][j];
                int newLen = getNewLen(i,k,j);
                graph[i][j] = min(oldLen, newLen);
            }
        }
    }
}
```

