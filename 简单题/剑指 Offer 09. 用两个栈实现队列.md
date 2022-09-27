# 題目描述:
## 用两个栈实现一个队列。队列的声明如下，请实现它的两个函数 appendTail 和 deleteHead ，分别完成在队列尾部插入整数和在队列头部删除整数的功能。(若队列中没有元素，deleteHead 操作返回 -1 )
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
### **备注**：用两个栈实现队列，一个栈存队列的值，调用头部时把栈的值倒入另一个栈即可。（其实没必要两个while...）
