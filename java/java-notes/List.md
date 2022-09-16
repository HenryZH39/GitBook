# List
### 1. List sort
- normal compare
```java
List<String> d = new ArrayList<>();
Collections.sort(d)
// REVERSE
Collections.sort(d, Collections.reverseOrder());
```
- customize comparator
```java
List<String> d = new ArrayList<>();
Collections.sort(d, new Comparator < String > () {
    public int compare(String s1, String s2) {
        return s1.length() != s2.length() ? s2.length() - s1.length() : s1.compareTo(s2);
    }
});
```