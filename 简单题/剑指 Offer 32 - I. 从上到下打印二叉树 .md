# 題目描述:
## 从上到下打印出二叉树的每个节点，同一层的节点按照从左到右的顺序打印。
### 我的题解：
```class Solution {
public:
    vector<int> levelOrder(TreeNode* root) {
        queue<TreeNode*> q1;
        q1.push(root);
        vector<int> result;
        if (root == NULL) return result;
        while (!q1.empty()) {
            int qSize = q1.size();
            for (int i = 0; i < qSize; i++) {
                TreeNode* t = q1.front();
                q1.pop();                
                result.push_back(t->val);
                if (t->left != NULL) q1.push(t->left);
                if (t->right != NULL) q1.push(t->right);
            } 
        } 
        return result;
    }
};
```
### **备注**：广搜实现层序遍历
        
