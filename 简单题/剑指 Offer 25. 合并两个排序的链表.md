# 題目描述:
## 输入两个递增排序的链表，合并这两个链表并使新链表中的节点仍然是递增排序的。
### 我的题解：
```class Solution {
public:
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
        ListNode* dummyHead = new ListNode(0);
        ListNode* newL = dummyHead;
        while (l1 != NULL && l2 != NULL) {
            if (l1->val > l2->val) {
                newL->next = l2;
                l2 = l2->next;
            } else if (l1->val <= l2->val) {
                newL->next = l1;
                l1 = l1->next;
            }
            newL = newL->next;
        }
        if (l1 == NULL) {
            newL->next = l2;
        } else if (l2 == NULL) {
            newL->next = l1;
        }
        return dummyHead->next;
    }
};
```
### **备注**：新建一个列表然后判断哪个链表的值大就加进去，最后还要判断哪个链表加完了，把另一个链表剩余部分接入
        
