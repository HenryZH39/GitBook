# Segment Tree
### Mutable tree build and udpate
- LeetCode[307. Range Sum Query - Mutable](https://leetcode.com/problems/range-sum-query-mutable/)
```java
class NumArray {
    class TreeNode {
        private int start, end, sum;
        private TreeNode left, right;
        public TreeNode(int start, int end) {
            this.start = start;
            this.end = end;
            this.left = left;
            this.right = right;
            this.sum = 0;
        }
    }
    private TreeNode root = null;

    public NumArray(int[] nums) {
        root = buildTree(nums, 0, nums.length - 1);
    }
    public TreeNode buildTree(int[] nums, int start, int end) {
        if (start > end) {
            return null;
        }
        TreeNode curr = new TreeNode(start, end);
        if (start == end) {
            curr.sum = nums[start]; // find the num as leaf
        } else {
            int mid = start + (end - start) / 2;
            curr.left = buildTree(nums, start, mid);
            curr.right = buildTree(nums, mid + 1, end);
            curr.sum = curr.left.sum + curr.right.sum;
        }
        return curr;    
    }
    
    public void update(int index, int val) {
        updateTree(root, index, val);
    }
    public void updateTree(TreeNode curr, int index, int val) {
        if (curr.left == curr.right) { // find the num
            curr.sum = val;
            return;
        }
        int mid = curr.start + (curr.end - curr.start) / 2;
        if (index <= mid) {
            updateTree(curr.left, index, val);
        } else {
            updateTree(curr.right, index, val);
        }
        curr.sum = curr.left.sum + curr.right.sum; 
    }
    
    public int sumRange(int left, int right) {
        return sumTree(root, left, right);
    }
    public int sumTree(TreeNode root, int start, int end) {
        if (root.start == start && root.end == end) {
            return root.sum;
        }
        int mid = root.start + (root.end - root.start) / 2;
        if (end <= mid) {
            return sumTree(root.left, start, end);
        } else if (mid < start) {
            return sumTree(root.right, start, end);
        } else {
            return sumTree(root.left, start, mid) + sumTree(root.right, mid + 1, end);
        }
    }
}
```