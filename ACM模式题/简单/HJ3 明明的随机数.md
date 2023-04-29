# 題目描述:
## 明明生成了NN个1到500之间的随机整数。请你删去其中重复的数字，即相同的数字只保留一个，把其余相同的数去掉，然后再把这些数从小到大排序，按照排好的顺序输出。
## 数据范围： 1 \le n \le 1000 \1≤n≤1000  ，输入的数字大小满足 1 \le val \le 500 \1≤val≤500 
### 我的題解：
```
#include <iostream>
#include <vector>
#include <algorithm>
#include <set>
using namespace std;

int main() {
    int n;
    cin>>n;
    int a;
    set<int> s1;
    for (int i = 0; i < n; i++) {
        cin>>a;
        s1.insert(a);
    };
    for (auto &s : s1) cout<<s<<endl;
    return 0;
}
```
### **备注**：排序+去重，直接set