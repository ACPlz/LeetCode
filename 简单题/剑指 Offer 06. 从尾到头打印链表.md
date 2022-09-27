# 题目描述
## 输入一个链表的头节点，从尾到头反过来返回每个节点的值（用数组返回）。
### 我的题解：
```class Solution {
public:
    vector<int> reversePrint(ListNode* head) {
        vector<int> result;
        while (head != NULL) {
            result.push_back(head->val);
            head = head->next;
        }
        reverse(result.begin(), result.end());
        return result;
    }
};
```
### **备注**：存入数组然后翻转一下
