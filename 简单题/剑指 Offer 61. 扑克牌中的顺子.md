# 題目描述:
## 从若干副扑克牌中随机抽 5 张牌，判断是不是一个顺子，即这5张牌是不是连续的。2～10为数字本身，A为1，J为11，Q为12，K为13，而大、小王为 0 ，可以看成任意数字。A 不能视为 14。
### 我的题解：
```class Solution {
public:
    bool isStraight(vector<int>& nums) {
        sort(nums.begin(), nums.end());
        int flag = 0;
        int count = 0;
        int temp = 0;
        for (int i = 0; i < nums.size() - 1; i++) {
            if (nums[i] == 0) {
                flag++;
                continue;
            }
            if (abs(nums[i] - nums[i + 1]) == 0) return false;
            else if (abs(nums[i] - nums[i + 1]) == 1) continue;
            else temp += abs(nums[i] - nums[i + 1]); 
        }
        if (flag >= temp - 1) return true;
        return false;
    }
};
```
### **备注**：先排序，记录大小王的个数，再记录相邻牌值的差值之和（若差值为1表示连续不记录，若为0则表示有重复的牌，直接return false）,最后判断大小王数量是否大于等于差值之和减一。
