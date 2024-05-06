---
title: PathCompression
date: 2024-03-11
category: [图,并查集]
---

- compress while `find()`

- code

  ```java
  class PathCompression implements DisjointSet{
      private int[] parents;
      Pathompresion(int size){
          parents = new int[size];
          for(int i=0;i<size;i+=1){
              parents[i] = i;
          }
      }
      public int find(int a){
          if(a != parents[a]){
              parents[a] = find(parents[a]);
          }
          return parents[a];
      }
  
      @Override
      public void connect(int a, int b){
          int aRoot = find(a);
          int bRoot = find(b);
          parents[aRoot] = bRoot;
      }
  
      @Override
      public boolean isConnected(int a, int b){
          return find(a)==find(b);
      }
  }
  ```

  