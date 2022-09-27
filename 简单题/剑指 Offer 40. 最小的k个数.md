# 題目描述:
## 输入整数数组 arr ，找出其中最小的 k 个数。例如，输入4、5、1、6、2、7、3、8这8个数字，则最小的4个数字是1、2、3、4。
### 我的题解：
```class Solution {
public:
    int partition(vector<int>& arr, int l, int r) {
        int left = l;
        int right = r;
        int privot = arr[left];
        while (left < right) {
            while (left < right && arr[right] >= privot) {
                right--;
            }
            while (left < right && arr[left] <= privot) {
                left++;
            }

            if (left < right) {
                swap(arr[left], arr[right]);
            }
        }
        swap(arr[l], arr[left]);
        return left;
    }
    void qSort(vector<int>& arr,int left, int right) {
        if (left >= right) return;
        int pivot = partition(arr, left, right);
        qSort(arr, left, pivot-1);
        qSort(arr, pivot + 1, right);
    }
    vector<int> getLeastNumbers(vector<int>& arr, int k) {
        vector<int> result = {};
        if (k == 0 || arr.size() == 0) return vector<int>();
        qSort(arr, 0, arr.size() - 1);
        for (int i = 0; i < k; i++) {
            result.push_back(arr[i]);
        }
        return result;
    }
};
```
### **备注**：用快排实现取前K个数，其实设置一个索引查找第k个就行了。
### 注意快排一定要从右边开始
