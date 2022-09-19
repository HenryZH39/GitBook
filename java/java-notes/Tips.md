# TIPS
### 1. Java Regular Expressions
- <a href = "https://www.w3schools.com/java/java_regex.asp"> Regular Expression </a>
  
### 2. Search in Rotated Sorted Array
- Leetcode [33. Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/)
```pseudo code
Formula: If a sorted array is shifted, if you take the middle, always one side will be sorted. Take the recursion according to that rule.

1- take the middle and compare with target, if matches return.  
2- if middle is bigger than left side, it means left is sorted  
2a- if [left] < target < [middle] then do recursion with left, middle - 1 (right)  
2b- left side is sorted, but target not in here, search on right side middle + 1 (left), right  
3- if middle is less than right side, it means right is sorted  
3a- if [middle] < target < [right] then do recursion with middle + 1 (left), right  
3b- right side is sorted, but target not in here, search on left side left, middle -1 (right)
```
### 3. Get random number in range
```java
	random.nextInt(max - min + 1) + min
```
or
```java
	Min + (int)(Math.random() * ((Max - Min) + 1))
```
### 4. Number of subarray
- For size N <br>
	the total of subarray = N x ( N + 1) / 2

### 5. Remove from ArrayList and LinkedList TC
- ArrayList:
  remove() : O(N)
- LinkedList :
  remove() : O(1)