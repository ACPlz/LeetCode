# 題目描述:
## 写出一个程序，接受一个由字母、数字和空格组成的字符串，和一个字符，然后输出输入字符串中该字符的出现次数。（不区分大小写字母）
### 我的題解：
```#include <iostream>
using namespace std;

int main() {
    string s;
    char s2;
    getline(cin, s);
    cin>>s2;
    int result = 0;
    for (int i = 0; i < s.length(); i++) {
        if (s[i] == s2 || s[i] == (s2 ^= 32)) result++;
    }
    cout<<result;
    return 0;
}
```
### **备注**：简单计数