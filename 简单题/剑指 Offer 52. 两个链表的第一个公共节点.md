# 題目描述:
## 输入两个链表，找出它们的第一个公共节点。
### 我的题解：
```cclass Solution {
public:
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        int flag = 0;
        if (headA == NULL || headB == NULL) return NULL;
        ListNode *head1 = headA;
        ListNode *head2 = headB;
        while (flag < 3) {
            if (headA == headB) return headA;
            if (headA->next != NULL) headA = headA->next;
            else {
                headA = head2;
                flag++;
            }
            if (headB->next != NULL) headB = headB->next;
            else {
                headB = head1;
                flag++;
            }
        }
        return NULL;
    }
};
```
### **备注**：由于m + n = n + m 所以让A链表遍历结束后再去遍历B链表，B链表遍历结束后指针去遍历A链表，如果有交叉两者一定会相遇