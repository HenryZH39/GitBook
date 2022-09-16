# Array
### 1. [Several sorting algorithms](../../algorithms/sorting-algorithm/README.md)
### 2. 2D Array Sorting
```java
Arrays.sort(envelopes, new Comparator<int[]>()
    {
        public int compare(int[] a, int[] b){
// if width are same , sorted decrasing by height ,otherwise sort increasing by width
            return a[0] == b[0]? b[1] - a[1] : a[0] - b[0];
        }
    });

Arrays.sort(points, (a,b) -> a[0] == b[0] ? 
            Integer.compare(a[1], b[1]) : Integer.compare(a[0], b[0]));
```
### 3. Int Array convert to ArrayList(Stream)
- Java8 stream
```java
int[] count = new int[n];
 List<Integer> res = Arrays.stream(count)
							.boxed()
							.collect(Collectors.toList());
```

### 4. Get Min & Max & Sum in Int Array (Stream)
```java
int[] tab = {12, 1, 21, 8};
int total = Arrays.stream(nums).sum();
int min = Arrays.stream(tab).min().getAsInt();
int max = Arrays.stream(tab).max().getAsInt();
```