### Union & Find

Union and Find is an algorithm that frequently used for graph/tree problems, especially in tree/graph validation, count the numbers of graph with a given adjacency map, find root parent of different nodes, etc.

Union & Find can be divided into two algorithm, **Union** and **Find**.

I will discuss two type of path compression implementations here.

**I'll probably discuss the trade off between path compression unionFind and regular unionFind in the future**


#### Node based
```Java
class Node<T> {
    T val;
    Node<T> parent;

    public Node(T val){
        this.val = val;
        this.parent = this;
    }

    public Node<T> find(){
        if(parent != this){
            this.parent = this.parent.find();
        }
        return this.parent;
    }

    //union a node to current node.
    public void union(Node<T> node){
        Node<T> selfParent = this.find();
        Node<T> nodeParent = node.find();

        nodeParent.parent = selfParent;
    }
}
```

#### Array Based
```java
/*
 * lets say there are N - 1 unique id;
 */
int[] parentMap = new int[n];

for(int i = 0; i < n; parentMap[i] = i, i++)

// return the id of the root parent
public int find(int nodeId){
    if(parentMap[nodeId] != nodeId){
        parentMap[nodeId] = find(parentMap[nodeId]);
    }
    return parentMap[nodeId];
}

// union j into i by their id.
public void union(int i, int j){
    int rootI = find(i);
    int rootJ = find(j);
    parentMap[rootJ] = rootI;
}
```
__Note:__ 
 * This method can be used only if each node has a **unique positive numerial id**.
