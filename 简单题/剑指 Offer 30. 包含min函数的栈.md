# 題目描述:
## 定义栈的数据结构，请在该类型中实现一个能够得到栈的最小元素的 min 函数在该栈中，调用 min、push 及 pop 的时间复杂度都是 O(1)。
### 我的题解：
```class MinStack {
public:
    /** initialize your data structure here. */
    MinStack() {

    }
    
    void push(int x) {
        st1.push(x);
        if (st2.empty()) st2.push(x);
        else if (st2.top() >= x) {
            st2.push(x);
        } else st2.push(st2.top());
    }
    
    void pop() {
        st1.pop();
        st2.pop();
    }
    
    int top() {
        return st1.top();
    }
    
    int min() {
        return st2.top();
    }
private:
    stack<int> st1;
    stack<int> st2;
};
```
### **备注**：由于要求时间复杂度要O(1)，所以使用一个辅助栈用于存储栈内的最小值。
### 当st1中的值更大时不用压入辅助栈中，但是为了pop(）不用再判断一下，可以压入辅助栈的栈顶元素。
        
