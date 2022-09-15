# Page 1

**4. Bubble Sort**

* Best case TC : O(N )
* Average case TC : O(N ^ 2)
* Worst case TC: O(N ^ 2)

```java
class Solution {
    public int[] sortArray(int[] nums) {
        if (nums == null || nums.length == 0) {
            return nums;
        }
        bubbleSort(nums);
        return nums;
    }
    public void bubbleSort(int[] nums) {
        int n = nums.length;
        for (int i = 0; i < n - 1; i++) {
            for (int j = 0; j < n - i - 1; j++) {
                if (nums[j] > nums[j + 1]) {
                    swap(j, j + 1, nums);
                }
            }
        }
    }
    public void swap(int i, int j, int[] nums) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
}
```

**5. Selection Sort**

* Average case TC : O(N ^ 2)
* Worst case TC: O(N ^ 2)

```java
class Solution {
	int n
    public int[] sortArray(int[] nums) {
        if (nums == null || nums.length == 0) {
            return null;
        }
        n = nums.length;
        selectionSor(nums);
        return nums;
    }
    public void selectionSort(int[] nums) {
        for (int i = 0; i < n - 1; i++) {
            min_index = i;
            for (int j = i + 1; j < n; j++) {
                if (nums[j] < nums[min_index]) {
                    min_index = j;
                } 
            }
            swap(nums, min_index, i);
        }
    }
    public void swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
}
```

**6. Insertion Sort**

* Average case TC : O(N ^ 2)
* Worst case TC: O(N ^ 2)

```java
class Solution {
    public int[] sortArray(int[] nums) {
        if (nums == null || nums.length == 0) {
            return null;
        }
        insertionSort(nums);
        return nums;
    }
    public void insertionSort(int[] nums) {
        for (int i = 1; i< nums.length; i++) {
            for (int j = i; j >= 1; j--) {
                if (nums[j] >= nums[j - 1]) {
                    break;
                }
                swap(nums, j, j - 1);
            }
        }
    }
    public void swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
}
```

**7. Bucket Sort**

* Best case TC : O(N + K)
* Average case TC : O(N + K)
* Worst case TC: O(N ^ 2)
* Space Complexity: O(N \* K)

```java
class Solution {
    public int[] sortArray(int[] nums) {
        if (nums == null || nums.length == 0) {
            return nums;
        }
        int max = Arrays.stream(nums).max().getAsInt();
        bucketSort(nums, max + 1);
        return nums;
    }
    public void bucketSort(int[] nums, int max) {
        int[] buckets = new int[max];
        //count 
        for (int i = 0; i < nums.length; i++) {
            buckets[nums[i]]++;
        }
        //sort
        for (int i = 0, j = 0; i < max; i++) {
            while ((buckets[i]--) > 0) {
                nums[j++] = i;
            }
        }
    }
}
```
