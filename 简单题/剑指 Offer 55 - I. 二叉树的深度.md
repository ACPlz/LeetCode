# 題目描述:
## 输入一棵二叉树的根节点，求该树的深度。从根节点到叶节点依次经过的节点（含根、叶节点）形成树的一条路径，最长路径的长度为树的深度。
### 我的题解：
```class Solution {
public:
    int maxDepth(TreeNode* root) {
        if (root == NULL) return 0;
        int left = maxDepth(root->left);
        int right = maxDepth(root->right);
        int res = max(left, right);
        return res + 1;
    } 
};
```
### **备注**：记录左右子树的最大深度然后回溯加一就行
        
