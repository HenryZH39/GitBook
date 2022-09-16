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
### 2. ArrayList Iteration 
- could use Iterator
```java
Iterator<Item> iter = list.iterator();
while(iter.hasNext()) {
  Item blah = iter.next();
  if(...) {
    iter.remove(); // Removes the 'current' item
  }
}
```
- could also reverse order loop
```java
for (char c : s.toCharArray()) {
	// reference will change after clear(). ArrayList copy should use clone()
	ArrayList<Node> check = (ArrayList) curr_char.get(c - 'a').clone();
	curr_char.get(c - 'a').clear();
	for (int i = check.size() - 1; i >= 0; i--) {
		Node node = check.get(i);
		node.index++;
		int next_index = node.index;
		if (next_index == node.word.length()) {
			count++;
		} else {
			char next_char = node.word.charAt(next_index);
			curr_char.get(next_char - 'a').add(node);
		}
	}
	check.clear();
}
```