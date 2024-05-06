---
title: QuickFind
date: 2023-08-01
category: [图,并查集]
---

## ListOfSetDS

To make a list of sets,to store the connections

*DISADVANTAGE: Too slow		O(N)



## QuickFind Version

![chrome_afyCps0cDW](images/QuickFind/chrome_afyCps0cDW.png)

Although the abstract concept of ***"Using set to stand for connection"*** is still the same, we can actually use a relatively abstract way to express the 

***"Set-Element Corresponding Relation"*** i.e. use an array of id. The **index-of-array** stands for the **element**, the **item-of-array** stands for **id-of-set**.

[RESTRICTION: only apply for INTERGERS]

![o.o.g](images/QuickFind/chrome_6OH84JBj31.png)



## Src

```java
public class QuickFind implements DisjointSets{
    private int[] id;
    QuickFind(int size){
        this.id = new int[size];
        for(int i = 0; i < size; i++){
            id[i] = i;
        }
    }
    @Override
    public void connect(int p, int q){
        int pid = id[p];
        int qid = id[q];
        for(int i = 0; i < id.length; i += 1){
            if(id[i] == qid){
                id[i] = pid;
            }
        }
    }
    @Override
    public boolean isConnected(int p, int q){
        return (id[p] == id[q]);
    }
}

```



