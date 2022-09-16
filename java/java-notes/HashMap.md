# HashMap
### 1. Sort HashMap
- Sort by value
```java
Map<String, Integer> sorted = new HashMap<>();
sorted = map
        .entrySet()
        .stream()
        .sorted(Map.Entry.comparingByValue())
        // decresing order
        // .sorted(Collections.reverseOrder(Map.Entry.comparingByValue()))
        .collect(
	       Collectors.toMap(Map.Entry::getKey,Map.Entry::getValue, (e1, e2) -> e2,
                LinkedHashMap::new));
```

- Sort by key (***could also use TreeMap***)  <a href="https://docs.oracle.com/javase/8/docs/api/java/util/TreeMap.html">link</a>
```java
Map<String, Integer> sorted = new HashMap<>();
sorted = map
        .entrySet()
        .stream()
        .sorted(Map.Entry.comparingByKey())
        // decresing order
        // .sorted(Collections.reverseOrder(Map.Entry.comparingByKey()))
        .collect(
            Collectors.toMap(Map.Entry::getKey,Map.Entry::getValue, (e1, e2) -> e2,
                LinkedHashMap::new));
```
### 2. TreeMap
- Sorted key map
```java
TreeMap<Integer, Integer> map = new TreeMap();

// Returns a key-value mapping associated with the least key greater than or equal to the given key, or null if there is no such key.
map.ceilingEntry(2); 

//Returns the least key greater than or equal to the given key, or null if there is no such key.
map.ceilingKey(2);

//Returns a reverse order NavigableSet view of the keys contained in this map.
map.descendingKeySet();

//Returns a key-value mapping associated with the least key in this map, or null if the map is empty.
map.firstEntry();

//Returns the first (lowest) key currently in this map.
map.firstKey();

//Returns the greatest key less than or equal to the given key, or null if there is no such key.
map.floorKey();

//Returns the least key strictly greater than the given key, or null if there is no such key.
map.higherKey();

//Returns the last (highest) key currently in this map.
map.lastKey();

//Returns the greatest key strictly less than the given key, or null if there is no such key.
map.lowerKey(2);
```