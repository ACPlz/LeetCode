# 题目描述
## 输入两棵二叉树A和B，判断B是不是A的子结构。(约定空树不是任意一个树的子结构)
## B是A的子结构， 即 A中有出现和B相同的结构和节点值。
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
### **备注**：递归判断B是否是A的子结构，终止条件为B为空或者A为空或者AB的值不相等的时候
### 逐一将A的每个点都与B进行判断。