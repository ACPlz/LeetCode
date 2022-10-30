# 题目描述
## 请实现一个函数，把字符串 s 中的每个空格替换成"%20"。
### 我的题解：
```class Solution {
public:
    string replaceSpace(string s) {
        int count = 0;
        int j;
        int i;
        for (int i = 0; i < s.length(); i++) {
            if (s[i] == ' ') {
                count += 2;
            }
        }      
        count += s.length();
        j = count - 1;
        i = s.length() - 1;//注意两边都要减一不然会越界
        s.resize(count);//resize函数重塑数组大小
        while (j > i) {
            if (s[i] != ' ') {
                s[j--] = s[i--];                      
            }
            else {
                s[j] = '0';
                s[j - 1] = '2';
                s[j - 2] = '%';
                i--;
                j -= 3;               
            }
        }
        return s;
    }
};
```
### **备注**：替换字符串中的字符，实际上可以使用replace函数直接替换。
### resize函数用于数组的扩容
### 注意while语句直接判断i != 0的话会导致空集以及第一位为空格的时候漏掉
***
### 二刷，扩容字符串，从右向左双指针
```class Solution {
public:
    string replaceSpace(string s) {
        int count = 0;
        for (int i = 0; i < s.length(); i++) {
            if (s[i] == ' ') count++;
        }
        int left = s.length() - 1;
        s.resize(s.length() + 2 * count);
        int right = s.length() - 1;
        while (left >= 0) {
            if (s[left] == ' ') {
                s[right--] = '0';
                s[right--] = '2';
                s[right--] = '%';
            } else {
                s[right--] = s[left];
            }
            left--;
        }
        return s;
    }
};
```
