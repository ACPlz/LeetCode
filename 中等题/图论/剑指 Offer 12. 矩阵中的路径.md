# 题目描述
## 给定一个 m x n 二维字符网格 board 和一个字符串单词 word 。如果 word 存在于网格中，返回 true ；否则，返回 false 。
## 单词必须按照字母顺序，通过相邻的单元格内的字母构成，其中“相邻”单元格是那些水平相邻或垂直相邻的单元格。同一个单元格内的字母不允许被重复使用。
### 我的题解：
```
class Solution {
public:
    bool dfs(int row, int col, int k, vector<vector<char>>& board, string word) {
        if (row < 0 || row >= n || col < 0 || col >= m || board[row][col] != word[k]) return false;
        if (k == word.length() - 1) return true;
        board[row][col] = '.';
        bool res = dfs(row - 1, col, k + 1, board, word) || dfs(row + 1, col, k + 1, board, word) || dfs(row, col - 1, k + 1, board, word) || dfs(row, col + 1, k + 1, board, word);
        board[row][col] = word[k];
        return res;
    }
    bool exist(vector<vector<char>>& board, string word) {
        n = board.size();
        m = board[0].size();
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++)  {
                if (dfs(i, j, 0, board, word)) return true;
            }
        }
        return false;
    }
private:
        int n,m;
};
```
### **备注**：深搜，逐个单词判断是否和目标字符串相等，因为加了一句不匹配直接返回所以标记点只要将访问过的点设置为一个不可能匹配的点就行了。