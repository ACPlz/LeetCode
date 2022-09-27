# 題目描述:
## 给定一个数组 A[0,1,…,n-1]，请构建一个数组 B[0,1,…,n-1]，其中 B[i] 的值是数组 A 中除了下标 i 以外的元素的积, 即 B[i]=A[0]×A[1]×…×A[i-1]×A[i+1]×…×A[n-1]。不能使用除法。
### 我的题解：
```class Solution {
public:
    vector<int> constructArr(vector<int>& a) {
        vector<int> temp(a.size(), 0);
        vector<int> b(a.size(), 0);
        if (a.size() == 0) return b;
        temp[a.size() - 1] = 1;
        b[0] = 1;
        for (int i = 1; i < a.size(); i++) {
            b[i] = b[i - 1] * a[i - 1];
        }
        for (int i = a.size() - 2; i >= 0; i--) {
            temp[i] = a[i + 1] * temp[i + 1];
        }
        for (int i = 0; i < a.size(); i++) {
            b[i] = b[i] * temp[i];
        }
        return b;
    }
};
```
### **备注**：由于题目标明不能用除法，所以用左乘右的方法来求解。建立两个数组，其中一个从左开始累乘到右，另一个从右开始累乘到左，最后将对应序号相乘即可。
        
