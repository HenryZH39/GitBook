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