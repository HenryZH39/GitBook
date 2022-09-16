# Backtracking
***Time complexity O(N!) (factorial of N)***
本质就是DFS的暴力枚举，3个问题：
- 路径
- 选择列表
- 结束条件
```psudo
result = []
def backtrack(路径, 选择列表):
	if 满足结束条件:
		result.add(路径)
		return
	for 选择 in 选择列表:
		做选择
		backtrack(路径, 选择列表)
		撤销选择
```
- Example : LeetCode[37. Sudoku Solver](https://leetcode.com/problems/sudoku-solver/)
```java
class Solution {
    public void solveSudoku(char[][] board) {
        if (board == null || board.length == 0) {
            return;
        }
        backtrack(board);
    }
    public boolean backtrack(char[][] board) {
        for (int row = 0; row < 9; row++) {
            for (int col = 0; col < 9; col++) {
                if (board[row][col] != '.') {
                    continue;
                }
                for (char k = '1'; k <= '9'; k++) {
                    if (isValidSudoku(row, col, k, board)) {
                        board[row][col] = k;
                        if (backtrack(board)) { // found the fit one 
                            return true;
                        }
                        board[row][col] = '.';
                    }
                }
                return false;
            }
        }
        return true;
    }
    public boolean isValidSudoku(int row ,int col, char val, char[][] board) {
        int startRow = (row / 3) * 3;
        int startCol = (col / 3) * 3;
        for (int i = 0; i < 9; i++) {
            if (board[row][i] == val) {
                return false;
            }
            if (board[i][col] == val) {
                return false;
            }
            if (board[startRow + i / 3][startCol + i % 3] == val) {
                return false;
            }
        }
        return true;
    }
}
```