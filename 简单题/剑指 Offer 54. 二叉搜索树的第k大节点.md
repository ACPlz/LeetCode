# 題目描述:
## 给定一棵二叉搜索树，请找出其中第 k 大的节点的值。
### 我的题解：
```class Solution {
public:
    void backtraval(TreeNode* root) {
        if (root == NULL) return;
        if (root->right)  backtraval(root->right);
        k2--;
        if (k2 == 0) res = root->val;
        if (root->left) backtraval(root->left);
    }
    int kthLargest(TreeNode* root, int k) {
        k2 = k;
        backtraval(root);
        return res;
    }
private:
    int k2 = 0;
    int res = 0;
};
```
### **备注**：二叉搜索树，按中序遍历的倒叙遍历，每经过一个点就记录第几次，第K次时记录该点数据即为结果。
        
