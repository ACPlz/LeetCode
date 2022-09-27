# 题目描述
## 请实现 copyRandomList 函数，复制一个复杂链表。在复杂链表中，每个节点除了有一个 next 指针指向下一个节点，还有一个 random 指针指向链表中的任意节点或者 null。
### 我的题解：
```class Solution {
public:
    Node* copyRandomList(Node* head) {
        map<Node*, Node*> mapNode;
        if (head == NULL) return NULL;
        Node* cur = head;
        while (cur != NULL) {
            Node* newNode = new Node(cur->val);
            mapNode[cur] = newNode;
            cur = cur->next;
        }
        cur = head;
        while (cur != NULL) {
            mapNode[cur]->next = mapNode[cur->next];
            mapNode[cur]->random = mapNode[cur->random];
            cur = cur->next;
        }
        return mapNode[head];
    }
};
```
### **备注**：由于要拷贝一个链表，且该链表有一个随机的指针指向随机地址，所以不能普通的拷贝。
### 因为随机指针指向的地址有可能未创建，所以需要提前创建好拷贝的链表地址。
### 因此正好满足一一对应的关系，所以利用哈希表存入原链表和拷贝链表一一对应的关系，最后再连起来就行。
### 其实还可以把拷贝的链表插入到原链表中间，最后再断开。