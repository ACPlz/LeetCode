# 題目描述:
## 定义一个函数，输入一个链表的头节点，反转该链表并输出反转后链表的头节点。
### 我的题解：
```class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        if (head == NULL || head->next == NULL) return head;
        ListNode* cur = reverseList(head->next);
        head->next->next = head;
        head->next = NULL;
        return cur;
    }
};
```
### **备注**：递归实现链表翻转，其中cur一直指的是最后的节点，之后head递归从后向前遍历每个节点并更改其指向
        
