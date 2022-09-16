# K Sum for K arrays (with HashMap)
[454. 4Sum II](https://leetcode.com/problems/4sum-ii/)
- Using hashmap save 一半数组和的 frequency and find the rest half 
- Time and Space : O(n ^ (k / 2))
```java
public int KSumCount(int[] nums1, int[] nums2, int[] nums3, int[] nums4) {
	int[][] lists = new int[][]{nums1, nums2, nums3, nums4};
	// save half numbers of arrays sum frequency
	Map<Integer, Integer> halfSumFreq = new HashMap<>();
	addToHash(lists, halfSumFreq, 0, 0);
	return findTarget(lists, halfSumFreq, lists.length / 2, 0);
}

public void addToHash(int[][] lists, Map<Integer, Integer> halfSumFreq, int index, int sum) {
	if (index == lists.length / 2) {
		int freq = halfSumFreq.getOrDefault(sum, 0);
		halfSumFreq.put(sum, freq + 1);
	} else {
		for (int num : lists[index]) {
			addToHash(lists, halfSumFreq, index + 1, sum + num);
		}
	}
}

public int findTarget(int[][] lists, Map<Integer, Integer> halfSumFreq, 
					  int index, int target) {
	if (index == lists.length) {
		return halfSumFreq.getOrDefault(target, 0);
	}
	int count = 0;
	for (int num : lists[index]) {
		count += findTarget(lists, halfSumFreq, index + 1, target - num );
	}
	return count;
}
```