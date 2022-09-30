# Stack & Queue
### 1. Detail
- [Official Doc](https://docs.oracle.com/javase/7/docs/api/java/util/Deque.html)
- Initial
```java
Deque<String> help = new ArrayDeque<>();
```
- Stack : Last - in - First - out
```java
help.push(a);
help.addFirst(a);

help.pop();
help.removeFirst();

help.peek();
help.peekFirst();
```
- Queue: First - in - First -out
```java
help.add(a);
help.addLast(a);

help.offer(a);
help.offerLast(a);

help.remove();
help.removeFirst()l

help.poll();
help.elemnet();
help.peek();
```