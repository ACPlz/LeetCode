# 題目描述:
## 数组中有一个数字出现的次数超过数组长度的一半，请找出这个数字。
### 我的题解：
```class Solution {
public:
    int majorityElement(vector<int>& nums) {
        unordered_map<int, int> map;
        int temp;
        for (int i = 0; i < nums.size(); i++) {
            map[nums[i]]++;
            if (map[nums[i]] > nums.size() / 2)  {
                temp = i;
                break;
            }
        } 
        return nums[temp];
    }
};
```
### **备注**：map存储数据，若大于数组长度一半则输出当前编号的值。
### 该方法空间复杂度高，可以采用摩尔投票法，循环过一遍每次出现则加一，遇到其他值则减一，若小于0则换成当前这个数。
### 还可以排序后直接取中位数。
        
