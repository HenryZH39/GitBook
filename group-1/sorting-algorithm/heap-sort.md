# Heap Sort

* Worst case TC: O(N \* logN)
* Should understand [Binary Heap](https://www.geeksforgeeks.org/binary-heap/)
  * The root element will be at Arr\[0].
  * The indexes of other nodes for the ith node, i.e., Arr\[i] :
    * Arr\[ ( i - 1 ) / 2] Returns the parent node
    * Arr\[ ( 2 \* i ) + 1] Returns the left child node
    * Arr\[ ( 2 \* i ) + 2] Returns the right child node

```java
class Solution {
    public int[] sortArray(int[] nums) {
        if (nums == null || nums.length == 0) {
            return nums;
        }
        heapSort(nums);
        return nums;
    }
    
    public void heapSort(int[] nums) {
        int n = nums.length;
        // Build heap
        for (int i = n / 2 - 1; i >= 0; i--) {
            heapify(nums, i, n - 1);
        }
        // One by one extract element from heap
        for (int i = n - 1; i >= 0; i--) {
            swap(nums, 0, i);
            heapify(nums, 0, i - 1);
        }
    }
    // To heapify a subtree rooted with node i 
    // which is an index in arr[]. n is size of heap
    public void heapify (int[] nums, int i, int end) {
        while (i <= end) {
            int left = 2 * i + 1;
            int right = 2 * i + 2;
            // the root index 
            int rootIndex = i;
            if (left <= end && nums[left] > nums[rootIndex]) {
                rootIndex = left;
            }
            if (right <= end && nums[right] > nums[rootIndex]) {
                rootIndex = right;
            }
            if (rootIndex == i) {
                break;
            }
            swap(nums, i, rootIndex);
            i = rootIndex;
        }
    }
    
    public void swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
}
```
