# 题目描述
## 实现 strStr() 函数。
## 给你两个字符串 haystack 和 needle ，请你在 haystack 字符串中找出 needle 字符串出现的第一个位置（下标从 0 开始）。如果不存在，则返回  -1 。
### 我的题解：
```
class Solution {
public:
    void getNext(int* next, string s) {
        int j = -1;
        next[0] = -1;
        for (int i = 1; i < s.length(); i++){
            while ((j >= 0) && (s[i] != s[j+1])) {
                j = next[j];
            }
            if (s[i] == s[j+1]) {
                j++;
            }
            next[i] = j;
        }
    }
    int strStr(string haystack, string needle) {
        if (needle.size() == 0) {
            return 0;
        }
        int next[needle.size()];
        int j = -1;
        getNext(next, needle);
        for (int i = 0; i < haystack.size(); i++) {
            while ((j >= 0) && (haystack[i] != needle[j+1])) {
                j = next[j];
            }
            if (haystack[i] == needle[j+1]) {
                j++;
            }
            if (j == needle.size() - 1) {
                return i - needle.size() + 1;
            }
        }
        return -1;
    }
};
```
### **备注**：字符匹配问题，虽然是简单题，但是由于使用了KMP算法所以归类到中等题上
### 需要注意的是，构造next数组时采用的方法是将前缀表统一减一，否则会出现next[j] = j一直为一个值的情况，陷入死循环。
### 而统一减一的时候需要注意j并不会代表字符匹配的长度了，需要+1.