# 題目描述:
## 输入一个整数数组，判断该数组是不是某二叉搜索树的后序遍历结果。如果是则返回 true，否则返回 false。假设输入的数组的任意两个数字都互不相同。
### 我的題解：
```class Solution {
public:
    bool verifyPostorder(vector<int>& postorder) {
        return tarvel(postorder, 0, postorder.size() - 1);
    }
    bool tarvel(vector<int>& postorder, int left, int right){
        if (left >= right) return true;
        int root = postorder[right];
        int medium = left;
        while (postorder[medium] < root) {
            medium++;
        }
        int startleft = medium;
        while (startleft < right) {
            startleft++;
            if (postorder[startleft] < postorder[right]) return false;
        }
        return tarvel(postorder, left, medium - 1) && tarvel(postorder, medium, right - 1);
    }
};
```
### **备注**：后序遍历最后一个节点为根节点，寻找之前出现过第一个大于根节点的值，则该值的左边为其左子树要全部小于根节点，右边则要大于根节点 ，递归判断即可，如果发现不是这样就返回错误。
