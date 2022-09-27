# 題目描述:
## 输入一个链表，输出该链表中倒数第k个节点。为了符合大多数人的习惯，本题从1开始计数，即链表的尾节点是倒数第1个节点。
## 例如，一个链表有 6 个节点，从头节点开始，它们的值依次是 1、2、3、4、5、6。这个链表的倒数第 3 个节点是值为 4 的节点。
### 我的题解：
```class Solution {
public:
    ListNode* getKthFromEnd(ListNode* head, int k) {
        ListNode* pre = head;
        ListNode* cur = head;
        for (int i = 0; i < k; i++) {
            cur = cur->next;
        }
        while (cur != NULL) {
            cur = cur->next;
            pre = pre->next;
        }
        return pre;
    }
};
```
### **备注**：双指针法，后一指针先前进k步，然后两指针同时前进，后一指针为NULL时输出前一指针。
        
