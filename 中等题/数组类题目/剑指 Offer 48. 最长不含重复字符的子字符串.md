# 题目描述
## 请从字符串中找出一个最长的不包含重复字符的子字符串，计算该最长子字符串的长度。
### 我的题解：
```
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        unordered_map<char, int> m1;
        int slow = 0;
        int result = 0;
        int len = 0;
        for (int i = 0; i < s.length(); i++) {
            if (m1[s[i]] == 0) {
                len++;
                m1[s[i]]++;
            } else {
                while (m1[s[i]] != 0) {
                    m1[s[slow]]--;
                    slow++;
                    len--;
                }
                m1[s[i]]++;
                len++;
            }
            result = max(len, result);
        }
        return result;
    }
};
```
### **备注**：滑动窗口，哈希表保证窗口内的元素一定唯一