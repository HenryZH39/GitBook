# BFS
```java
如果不需要确定当前遍历到了哪一层:

while queue 不空：

    cur = queue.pop()

    for 节点 in cur的所有相邻节点：

        if 该节点有效且未访问过：

            queue.push(该节点)

如果要确定当前遍历到了哪一层:

level = 0

while queue 不空：

    size = queue.size()

    while (size --) {

        cur = queue.pop()

        for 节点 in cur的所有相邻节点：

            if 该节点有效且未被访问过：

                queue.push(该节点)10new

    }

level ++;
```
