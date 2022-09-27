# 題目描述:
## 从上到下按层打印二叉树，同一层的节点按从左到右的顺序打印，每一层打印到一行。
### 我的题解：
```class Solution {
public:
    vector<vector<int>> levelOrder(TreeNode* root) {
        vector<vector<int>> result;
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
            result.push_back(temp);
        }
        return result;
    }
};
```
### **备注**：广搜实现层序遍历，然后用temp暂存每一行最后存到result中
        
