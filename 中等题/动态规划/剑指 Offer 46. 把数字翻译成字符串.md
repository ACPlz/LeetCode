# 题目描述
## 给定一个数字，我们按照如下规则把它翻译为字符串：0 翻译成 “a” ，1 翻译成 “b”，……，11 翻译成 “l”，……，25 翻译成 “z”。一个数字可能有多个翻译。请编程实现一个函数，用来计算一个数字有多少种不同的翻译方法。
### 我的题解：
```
class Solution {
public:
    int translateNum(int num) {
        string str = to_string(num);
        vector<int> dp(str.length() + 1);
        if (str.length() == 0) return 0;
        if (str.length() == 1) return 1;
        if ((str[0] - '0') * 10 + (str[1] - '0') <= 25)  {
            dp[1] = 2;
        }
        else {
            dp[1] = 1;
        }
        if (str.length() == 2) return dp[1];
        dp[0] = 1;
        for (int i = 2; i < str.length(); i++) {
            int t = (str[i - 1] - '0') * 10 + (str[i] - '0');
           // cout<<t<<" ";
            if (t <= 25 && t >= 10) {
                dp[i] = dp[i - 1] + dp[i - 2];
            } else {
                dp[i] = dp[i - 1];
            }
            //cout<<dp[i];
        }
        return dp[str.length() - 1];
    }
};
```
### **备注**：DP问题，和跳楼梯有点像，dp[i]表示0-i可以翻译成多少个数，该状态只能由i-1或者i-2得来，当前数和上一个数若能组成一个数翻译，则可选择i-1即不连着翻译或者i-2即连着翻译两种状态；若不能组成，则等于上一状态