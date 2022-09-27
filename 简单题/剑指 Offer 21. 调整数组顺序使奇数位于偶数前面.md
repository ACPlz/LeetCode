# 題目描述:
## 输入一个整数数组，实现一个函数来调整该数组中数字的顺序，使得所有奇数在数组的前半部分，所有偶数在数组的后半部分。
### 我的题解：
```class Solution {
public:
    vector<int> exchange(vector<int>& nums) {
        int i = 0;
        int j = nums.size() - 1;
        while (i < j) {
            if (nums[i] % 2 == 0) {
                while (i < j && nums[j] % 2 == 0) {
                    j--;
                   // cout<<j;
                }
                swap(nums[i], nums[j]);
            }
            i++;
        }
        return nums;
    }
};
```
### **备注**：双指针法，俩指针一个前为偶后为奇则交换。
        
