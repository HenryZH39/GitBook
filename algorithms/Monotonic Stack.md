# Monotonic stack

- Save continue decreasing(or increasing) index when find the next large index .
- Example: 
  - LeetCode[739. Daily Temperatures](https://leetcode.com/problems/daily-temperatures/)
```java
class Solution {
    public int[] dailyTemperatures(int[] temp) {
        if (temp == null || temp.length == 0) {
            return new int[0];
        }
        int n = temp.length;
        int[] res = new int[n];
        Deque<Integer> stack = new ArrayDeque<>();
        for (int i = 0; i < n; i++) {
            while (!stack.isEmpty() && temp[stack.peek()] < temp[i]) {
                int index = stack.pop();
                res[index] = i - index;
            }
            stack.push(i);
        }
        return res;
    }
}
```
  - LeetCode[2281. Sum of Total Strength of Wizards](https://leetcode.com/problems/sum-of-total-strength-of-wizards/) It is also in my OA(Amazon SDEII)
