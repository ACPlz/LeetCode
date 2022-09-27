# 題目描述:
## 统计一个数字在排序数组中出现的次数。
### 我的题解：
```class Solution {
public:
    int backtravel(vector<int>& nums, int left, int right, int target) {
        int mid = left + (right - left) / 2;
        if (nums[mid] == target) return mid;
        if (left >= right) return -1;
        if (nums[mid] > target) return backtravel(nums, left, mid, target);
        else return backtravel(nums, mid + 1, right, target);
    }
    int search(vector<int>& nums, int target) {
        if (nums.size() == 0) return 0;
        int index = backtravel(nums, 0, nums.size() - 1, target);
        int res = 0;
        if (index == -1) return 0;
        for (int i = index + 1; i < nums.size(); i++) {
            if (nums[i] == nums[index]) res++;
        }
        for (int i = index; i >= 0; i--) {
            if (nums[i] == nums[index]) res++;
        }
        return res;
    }
};
```
### **备注**：显然是用二分法（注意用回溯写二分的时候要先判断中间点）
### 记得判断空集
        
