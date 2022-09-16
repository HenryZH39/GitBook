# Trie
### 1. Initial TrieNode
```java
public class TrieNode {
	int count;
	int prefix;
	TrieNode[] nextNode = new TrieNode[26];
	public TrieNode() {
		count = 0;
		prefix = 0;
	}
}
```
### 2. Insert a new string
```java
public static void insert(TrieNode root, String str) {
	if (root == null || str.length() == 0) {
		return;
	}
	char[] c = str.toCharArray();
	for (int i = 0; i < str.length(); i++) {
		// if not exist , creat a new TrieNode
		if (root.nextNode[c[i] - 'a'] == null) {
			root.nextNode[c[i] - 'a'] = new TrieNode();
		}
		root = root.NextNode[c[i] - 'a'];
		root.prefix++;
	}
}
```
### 3. Check the string exist . if have return numbers , if not return -1
```java
public static int search(TrieNode root, String str) {
	if (root == null || str.length() == 0) {
		return -1;
	}
	char[] c = str.toCharArray();
	for (int i = 0; i < str.length(); i++) {
		if (root.nextNode[c[i] - 'a'] == null) {
			return -1;
		}
		root = root.nextNode[c[i] - 'a'];
	}
	return root.count == 0 ? -1 : root.count;
}
```
### 4. Seach the number of words start with str
```java
public static int searchPreif(TrieNode root, String str) {
	if (root == null || str.length() == 0) {
		return -1;
	}
	char[] c = str.toCharArray();
	for (int i = 0; i < str.length(); i++) {
		if (root.nextNode[c[i] - 'a'] == null) {
			return -1;
		}
		root = root.nextNode[c[i] - 'a'];
	}
	return root.prefix;
}
```
### 5. Delete a word in Trie
```java
public static void delete(TrieNode root, String str){            
	if (str == null || root == null) return;  
    // 如果该前缀树中不存在该字符串，则直接返回            
	if (!search(root, str)) return;  
	char c[] = str.toCharArray();  
	for (int i = 0; i < c.length; i++){  
    // 遍历单词中的每一个字符，若当前字符不在前缀树中则为每一个字符建立一个分支
    if (--root.nexts[c[i] - 'a'].pass == 0){  
	    root.nexts[c[i] - 'a'] = null;  
        return;
	    }                        
    // 跳到前缀树的下一层                        
	    root = root.nexts[c[i] - 'a'];  
	}  
    root.end--;  
}
```