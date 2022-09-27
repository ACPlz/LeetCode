# 题目描述
## 把一个数组最开始的若干个元素搬到数组的末尾，我们称之为数组的旋转。
## 给你一个可能存在 重复 元素值的数组 numbers ，它原来是一个升序排列的数组，并按上述情形进行了一次旋转。请返回旋转数组的最小元素。例如，数组 [3,4,5,1,2] 为 [1,2,3,4,5] 的一次旋转，该数组的最小值为 1。  
### 我的题解：
```class Solution {
public:
    int minArray(vector<int>& numbers) {
        int l = 0, r = numbers.size() - 1;
        if (numbers[0] < numbers[r]) return numbers[0];
        while (l < r) {
            int mid = (l + r) / 2;
            //cout<<mid<<" ";
            if (numbers[mid] > numbers[r]) l = mid + 1;
            else if (numbers[mid] < numbers[r]) r = mid;
            else if (numbers[mid] == numbers[r]) r--; 
           
        }
        return numbers[r];
    }
};
```
### **备注**：二分法，把中间的数和右边的进行判断，如果大于右边，说明异常值在右边，小于右边说明异常值在左边，因为数字可以重复，数字重复时需要将右边值减一。
### 需要注意的是，因为是和右边的值在比，所以已经排除了中间值小于右边值的情况，所以只能是右边减一，不能是左边。
