# 題目描述:
## 在字符串 s 中找出第一个只出现一次的字符。如果没有，返回一个单空格。 s 只包含小写字母。
### 我的题解：
```class Solution {
public:
    char firstUniqChar(string s) {
        map<char, int> map1;
        for (int i = 0; i < s.length(); i++) {
            map1[s[i]]++;
        } 
        for (int i = 0; i < s.length(); i++) {
            if (map1[s[i]] == 1) {
                return s[i];
            } 
        }
        return ' ';
    }
};
```
### **备注**：map记录每个字符出现的次数，第二次遍历输出第一个等于一的字母
        
