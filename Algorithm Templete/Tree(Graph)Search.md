### DFS / BFS

#### Depth First Search (backtrack, path generation, longest distance, ...)
Basic Depth Search takes O(x^n) time complexity, x is the number of recursive calls in each call.

One special case is DFS for binary tree, which is O(n). The high of binary tree is ```log n```, and 2 recursive calls each level, O(2^(log n)) which is O(n).

```java
void dfs(int param){
    //End condition
    if(param < 0) return;

    //Reduce scope
    dfs(param - 1);
    dfs(param - 2);
}
```

#### DFS Tree Search (in-order, pre-order, post-order).
in-order, pre-order, and post-order are actually the special case of DFS. The only difference is when will the functional statements be executed.

**In-order (execute between two childs)**
```java
void dfs(int param){
    //End condition
    if(param < 0) return;

    //Reduce scope
    dfs(param - 1);
    //functional statement.
    System.out.println(param);
    dfs(param - 2);
}
```

**pre-order (execute before two childs)**
```java
void dfs(int param){
    //End condition
    if(param < 0) return;

    //functional statement.
    System.out.println(param);

    //Reduce scope
    dfs(param - 1);
    dfs(param - 2);
}
```

**post-order (execute after two childs)**
```java
void dfs(int param){
    //End condition
    if(param < 0) return;

    //Reduce scope
    dfs(param - 1);
    dfs(param - 2);

    //functional statement.
    System.out.println(param);
}
```

#### Breath First Search (shortest distance, path existence).
The basic version of breath first search is actually the same as **level-order search** of a tree.
```java
void bfs(Object obj){
    Queue queue;
    //initialization
    queue.add(obj);

    while(!queue.isEmpty){
        Object obj = queue.pop();

        //functional statement.
        System.out.println(obj.toString());

        //Add next level to queue.
        for(Object obj : obj.childs){
            queue.offer(obj);
        }
    }
}
```

#### Bidirectional BFS

```java
void bfs(Object start, Object end){
    Queue queueStart;
    Queue queueEnd;
    //initialization
    queueStart.add(start);
    queueEnd.add(end);


    while(!queue.isEmpty){

        if(queueStart.size() > queueEnd.size()){
            swap(queueStart, queueEnd);
        }

        Object obj = queue.pop();

        //Exit condition
        if(queueEnd.contains(obj)) return;

        //functional statement.
        System.out.println(obj.toString());

        //Add next level to queue.
        for(Object obj : obj.childs){
            queue.offer(obj);
        }
    }
}
```