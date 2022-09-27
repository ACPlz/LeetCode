# 題目描述:
## 给定单向链表的头指针和一个要删除的节点的值，定义一个函数删除该节点。
## 返回删除后的链表的头节点。
### 我的题解：
```class Solution {
public:
    ListNode* deleteNode(ListNode* head, int val) {
        ListNode* dummyHead = new ListNode(0);
        dummyHead->next = head;
        ListNode* cur = dummyHead;
        while(cur->next != NULL) {
            if (cur->next->val == val) {
                cur->next = cur->next->next;
                break;
            }
            cur = cur->next; 
        }
        return dummyHead->next;
    }
};
```
### **备注**：删除链表节点，用虚拟头结点，不用特意去判断头结点。
        
