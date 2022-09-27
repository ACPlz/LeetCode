# 题目描述
## 在数组中的两个数字，如果前面一个数字大于后面的数字，则这两个数字组成一个逆序对。输入一个数组，求出这个数组中的逆序对的总数。
### 我的题解：
```class Solution {
public:
    vector<int> tmp;
    int merge_sort(vector<int>& nums, int l, int r) {
        if (l >= r) return 0;
        int mid = l + (r - l) / 2;
        int res = merge_sort(nums, l, mid) + merge_sort(nums, mid + 1, r);
        int i = l, j = mid + 1, k = 0;
        while (i <= mid && j <= r) {
            if (nums[i] <= nums[j]) {
                tmp[k++] = nums[i++];
            } else {
                res += mid - i + 1;
                tmp[k++] = nums[j++];
            }
        }
        while (i <= mid) {
            tmp[k++] = nums[i++];
        }
        while (j <= r) {
            tmp[k++] = nums[j++];
        }
        for (int i = l, j = 0; i <= r; i++, j++) {
            nums[i] = tmp[j];
        }
        return res;
    }
    int reversePairs(vector<int>& nums) {
        int n = nums.size();
        tmp.resize(n);
        return merge_sort(nums, 0, nums.size() - 1);
    }
};
```
### **备注**：利用归并排序的思想计算逆序队
### 先将数据二分为左右两份 ，将其中一份作为比较，放如tmp数组的数据若比另一份更小则放入并将指针后移一位
### 如果更大，说明需要放后一份数据进去，且前一份数据都比后一份目前指针指向的数据更大，构成逆序对，res = mid - i +1;
### 最后返回res即可。