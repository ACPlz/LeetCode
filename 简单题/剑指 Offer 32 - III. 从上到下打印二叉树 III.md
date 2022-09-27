# 題目描述:
## 请实现一个函数按照之字形顺序打印二叉树，即第一行按照从左到右的顺序打印，第二层按照从右到左的顺序打印，第三行再按照从左到右的顺序打印，其他行以此类推。
### 我的题解：
```class Solution {
public:
    vector<vector<int>> levelOrder(TreeNode* root) {
        vector<vector<int>> result;
        int flag = 1;
        if (root == NULL) return result;
        queue<TreeNode*> q1;
        q1.push(root);
        while (!q1.empty()) {
            int size = q1.size();
            vector<int> temp;
            for (int i = 0; i < size; i++) {
                TreeNode* t = q1.front();
                q1.pop();
                temp.push_back(t->val);
                if (t->left != NULL) q1.push(t->left);
                if (t->right != NULL) q1.push(t->right);
            }
            if (flag == 0) {
                reverse(temp.begin(), temp.end());
                flag = 1;
            } else flag = 0;
            result.push_back(temp);
        }
        return result;
    }
};
```
### **备注**：广搜实现层序遍历，然后用temp暂存每一行最后存到result中
### 对奇数数组进行翻转即可
        
