# Set
### 1. TreeSet
- ceiling() : return the least element in this set greater than or equal to the given element, or null if there is no such element.
``` java
TreeSet<Integer> set = new TreeSet<>();
set.add(24);
set.add(30);
int value = set.ceiling(25); // return 30
```
- floor() : return the greatest element in this set less than or equal to the given element, or null if there is no such element.
```java
TreeSet<Integer> set = new TreeSet<>();
set.add(24);
set.add(30);
int value = set.floor(25); // return 24
```