# 題目描述:
## 输入一棵二叉搜索树，将该二叉搜索树转换成一个排序的循环双向链表。要求不能创建任何新的节点，只能调整树中节点指针的指向
### 我的題解：
```class Solution {
public:
    void travel(Node* cur) {
        if (cur == NULL) return;
        travel(cur->left);
        if (pre == NULL) head = cur; 
        else pre->right = cur;
        cur->left = pre;
        pre = cur;
        travel(cur->right);
    }
    Node* treeToDoublyList(Node* root) {
        if (root == NULL) return NULL;
        travel(root);
        head->left = pre;
        pre->right = head;
        return head;
    }
private:
    Node* pre = NULL;
    Node* head = NULL;
};
```
### **备注**：由于是二叉搜索树，中序遍历即可，特别要设立一个头结点（即遍历到最左侧节点时把当前节点记为头结点）
### 然后设立PRE节点记录上一个节点，将上一个节点链接到下一个节点
### 遍历完后将头尾链接
