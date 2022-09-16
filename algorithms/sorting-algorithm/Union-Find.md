# Union - Find
### 1. Concept
- [Reference video](https://www.youtube.com/watch?v=wU6udHRIkcc)
- **Find**: Determine which subset a particular element is in. This can be used for determining if two elements are in the same subset.
- **Union**: Join two subsets into a single subset. Here first we have to check if the two subsets belong to same set. If no, then we cannot perform union.
- find(u) 本质是找爸爸的爸爸 
```java
class Solution {
    private int n;  // 节点数量3 到 1000
    private int[] father;
    public Solution() {
        n = 1005;
        father = new int[n];
        // 并查集初始化
        for (int i = 0; i < n; ++i) {
            father[i] = i;
        }
    }
    // 并查集里寻根的过程
    private int find(int u) {
        if(u == father[u]) {
            return u;
        }
        father[u] = find(father[u]);
        return father[u];
    }
    // 将v->u 这条边加入并查集
    private void join(int u, int v) {
        u = find(u);
        v = find(v);
        if (u == v) return ;
        father[v] = u;
    }
    // 判断 u 和 v是否找到同一个根，本题用不上
    private Boolean same(int u, int v) {
        u = find(u);
        v = find(v);
        return u == v;
    }
    public int[] findRedundantConnection(int[][] edges) {
        for (int i = 0; i < edges.length; i++) {
            if (same(edges[i][0], edges[i][1])) {
                return edges[i];
            } else  {
                join(edges[i][0], edges[i][1]);
            }
        }
        return null;
    }
}
```

### 2. Optimization 
- [Definition](https://www.geeksforgeeks.org/union-find-algorithm-set-2-union-by-rank/)
- Union by rank
- Path Compression
```java
class Solution {
    class Node {
        int parent;
        int rank;
        public Node(int parent, int rank) {
            this.parent = parent;
            this.rank = rank;
        }
    }
    private int[][] isConnected;
    private Node[] parent;
    private int n, count;
    public int findCircleNum(int[][] isConnected) {
        if (isConnected == null || isConnected.length == 0 || isConnected[0].length == 0) {
            return 0;
        }
        this.isConnected = isConnected;
        this.n = isConnected.length;
        this.count = n;
        this.parent = new Node[n];
        for (int i = 0; i < n; i++) {
            parent[i] = new Node(i, 0);
        }
        for (int i = 0; i < n; i++) {
            for (int j = i + 1; j < isConnected[i].length; j++) {
                if (isConnected[i][j] == 1) {
                    union(i, j);
                }
            }
        }
        return count;
    }
    public void union(int u, int v) {
        u = find(u);
        v = find(v);
        if (u == v) {
            return;
        }
        if (parent[u].rank < parent[v].rank) {
            parent[u].parent = v;
        } else if (parent[u].rank > parent[v].rank) {
            parent[v].parent = u;
        } else {
            parent[v].parent = u;
            parent[u].rank++;
        }
        count--;
    }
    public int find(int x) {
        if (parent[x].parent != x) {
			//path compression
            return parent[x] = find(parent[x].parent);
        }
        return x;
    }
}
```