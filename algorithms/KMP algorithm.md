# String KMP algorithm
- code
```java
public int[] getLps(int n, String needle){
	int[] lps = new int[n];
	int j = 0;
	for (int i = 1; i < n; i++){
		while (j > 0 && needle.charAt(i) != needle.charAt(j)){
			j = lps[j - 1];
		}
		if (needle.charAt(i) == needle.charAt(j)){
			j++;
		}
		lps[i] = j;
	}
	return lps;

}
```