---
title: QuickUnion
date: 2023-08-01
category: [图,并查集]
---

## ROOT concept

It's a little bit like **SLList**, but in a shape of **tree** rather than **strip**

<img src="images/QuickUnion/9.3.1.png" alt="img" style="zoom:50%;" />



## Union

Let's say to run `connect(2,3)`:

The right way to do is `id[3] = find(2)`, instead of `id[3]=2` *// It's not wrong, but will make the tree too TALL!*



## Src

```java
public class QuickUnion implements DisjointSets{
    private int[] parent;
    QuickUnion(int size){
        this.parent = new int[size];
        for(int i = 0;i < size; i += 1){
            this.parent[i] = -1;
        };
    }
    private int find(int p){
        while(this.parent[p] >= 0){
            p = parent[p];
        }
        return p;
    }
    @Override
    public void connect(int p,int q){
        int pRoot = find(p);
        int qRoot = find(q);
        parent[pRoot] = qRoot;
    }
    @Override
    public boolean isConnected(int p,int q) {
        return (find(p) == find(q));
    }
}

```



## o.o.g

<img src="images/QuickUnion/chrome_5jfaNVvj3a.png" alt="chrome_5jfaNVvj3a" style="zoom: 67%;" />

- Why `connect()` in QuickUnion is **O(N)**: 
  - For the most special case, to connect A and B(when B is the second to last, and all element except for A is in 1 set), you have to go through about N times to find the root of B;

- Why `isConnected()` in QuickUnion is **O(N)**: alike above;







