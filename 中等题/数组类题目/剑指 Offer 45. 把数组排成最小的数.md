# 題目描述:
## 输入一个非负整数数组，把数组里所有数字拼接起来排成一个数，打印能拼接出的所有数字中最小的一个。
### 我的题解：
```class Solution {
public:
    int partition(vector<string>& strs, int left, int right) {
        int l = left;
        int r = right;
        string pivot = strs[left];
        while (l < r) {
            while (l < r && (strs[r] + pivot) >= (pivot + strs[r])) r--;
            while (l < r && (strs[l] + pivot) <= (pivot + strs[l])) l++;
            if (l < r) {
                swap(strs[r], strs[l]);
            }
        }
        swap(strs[left], strs[l]);
        return l;
    }
    void qSort(vector<string>& strs, int left, int right) {
        if (left >= right) return;
        int pivot = partition(strs, left, right);
        qSort(strs, left, pivot - 1);
        qSort(strs, pivot + 1, right);
    }
    string minNumber(vector<int>& nums) {
        vector<string> strs;
        for (int i = 0; i < nums.size(); i++) {
            strs.push_back(to_string(nums[i]));
        }
        qSort(strs, 0, nums.size() - 1);
        string result;
        for (int i = 0; i < strs.size(); i++) {
            result.append(strs[i]);
        }
        return result;       
    }
};
```
### **备注**：快排思想，选取中间值，将和中间值组合更大的数放在右边，更小的放在左边，最后将排序好的字符串数组转换为字符串输出即可。
        
