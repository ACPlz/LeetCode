# 題目描述:
## 输入一个递增排序的数组和一个数字s，在数组中查找两个数，使得它们的和正好是s。如果有多对数字的和等于s，则输出任意一对即可。
### 我的题解：
```class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        vector<int> result;
        if (nums.size() <= 1) return result; 
        int left = 0;
        int right = nums.size() - 1;
        while (nums[left] + nums[right] != target) {
            if (nums[left] + nums[right] < target) left++;
            else if (nums[left] + nums[right] > target) right--;  
        }
        result.push_back(nums[left]);
        result.push_back(nums[right]);
        return result;
    }
};
```
### **备注**：双指针法，头尾指针，大则右边左移，小则左边右移。
        
