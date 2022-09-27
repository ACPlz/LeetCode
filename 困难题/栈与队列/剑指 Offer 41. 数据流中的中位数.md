# 题目描述
## 如何得到一个数据流中的中位数？如果从数据流中读出奇数个数值，那么中位数就是所有数值排序之后位于中间的数值。如果从数据流中读出偶数个数值，那么中位数就是所有数值排序之后中间两个数的平均值。
### 我的题解：
```class MedianFinder {
public:
    /** initialize your data structure here. */
    priority_queue<int> big_heap;
    priority_queue<int, vector<int>, greater<int>> small_heap;
    MedianFinder() {

    }
    void addNum(int num) {
        if (small_heap.empty()) {
            small_heap.push(num);
            return;
        }
        if (big_heap.size() != small_heap.size()) { 
            small_heap.push(num);
            int t1 = small_heap.top();
            small_heap.pop();
            big_heap.push(t1);
        } else {
            big_heap.push(num);
            int t2 = big_heap.top();
            big_heap.pop();
            small_heap.push(t2);
        }
    }
    double findMedian() {
       if (big_heap.size() != small_heap.size()) {
           return small_heap.top();
       } else {
           return (double)(small_heap.top() + big_heap.top()) / 2;
       }
    }
};
```
### **备注**：利用优秀队列大顶堆小顶堆来实现
### 保证小顶堆个数 = 大顶堆 + 1
### 当两者个数不同则输出小顶堆堆顶，相同时则输入两者堆顶元素之和加一
### 特别需要注意的是，当加入元素时，不能直接将元素分配至某个堆中，因为有可能该元素在另一元素中并不位于堆顶，所以要先加入另一个堆，然后再弹出堆顶元素加入另一堆
### 最后要将输出的数转化为double