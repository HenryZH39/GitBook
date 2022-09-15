# BianrySearch

- 确定是[left , right ] 
```java
While (left <= right)
	Mid = left + (right – left)/2;
	if nums[mid] > target
		right = mid -1
	if num[mid] < target
		left = mid + 1
	find target
		return mid
```
- 确定是[left , right )
```java
While (left < right )
	Mid = left + (right – left)/2;
	if nums[mid] > target
		right = mid
	if num[mid] < target
		left = mid + 1
	find target
		return mid
```