# 題目描述:
## 输入一棵二叉树的根节点，判断该树是不是平衡二叉树。如果某二叉树中任意节点的左右子树的深度相差不超过1，那么它就是一棵平衡二叉树。
### 我的题解：
```class Solution {
public:
    int countHeight(TreeNode* root) {
        if (root == NULL) return 0;
        int left = countHeight(root->left);
        int right = countHeight(root->right);
        if (left == -1 || right == -1 || (abs(left - right) > 1)) {
            return -1;
        }
        return max(left, right) + 1;
    }
    bool isBalanced(TreeNode* root) {
        if (countHeight(root) >= 0) return true;
        else return false;
    }
};
```
### **备注**：自底而上遍历，对比左右数的深度超过1则判定不是返回-1；
        
