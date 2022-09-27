# 題目描述:
## 一个长度为n-1的递增排序数组中的所有数字都是唯一的，并且每个数字都在范围0～n-1之内。在范围0～n-1内的n个数字中有且只有一个数字不在该数组中，请找出这个数字。
### 我的题解：
```class Solution {
public:
    int missingNumber(vector<int>& nums) {
        int left = 0;
        int right = nums.size() - 1;
        if (nums.size() == 1) {
            if (nums[0] == 1) return 0;
            else return 1;
        }
        if (nums[nums.size() - 1] == (nums.size() - 1)) return nums.size();
        if (nums[0] == 1) return 0;
        int index = left + (right - left) / 2;
        while (left <= right) {
            int mid = left + (right - left) / 2;
            if (nums[mid] == mid) left = mid + 1;
            else right = mid - 1;
        }
        return left;
    }
};
```
### **备注**：二分法，判断当前值是否等于其索引值，不等说明该值在左边，相等说明该值在右边。
        
