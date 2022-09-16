# String
### 1. String management
```java
Char[] sa = s.toCharArray();
//operation
StringBuilder sb = new StringBuilder();
for (int i = 0; i < sa.length; i++) {
	sb.append(sa[i]);
}
return sb.toString();
```
- eliminates leading and trailing spaces
```java
String str1 = "  Hello World  ";
str1.trim();
```