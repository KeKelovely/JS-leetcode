[Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/description/)

### 问题描述
Given two sorted integer arrays nums1 and nums2, merge nums2 into nums1 as one sorted array.

Note:
You may assume that nums1 has enough space (size that is greater or equal to m + n) to hold additional elements from nums2. The number of elements initialized in nums1 and nums2 are m and n respectively.

### 解法：
1. 注意本题的条件限制，必须在nums1上进行操作，应该是不允许使用额外的空间。
2. 所以本题就在nums1的基础上进行归并排序，从两数组合并后m+n-1的尾部开始，比较大小，然后填入相应元素，分为两种情况：
- 填充完毕后，若nums1元素还有剩余，nums2元素用完，那么剩下nums1的元素会自动排好（因为本来就在原来的位置上），不需要调整
- 若nums2元素有剩余，nums1元素用完，说明还有余下的nums2元素需要插入，这时直接插入操作即可。

### 源码实现
```
/**
 * @param {number[]} nums1
 * @param {number} m
 * @param {number[]} nums2
 * @param {number} n
 * @return {void} Do not return anything, modify nums1 in-place instead.
 */
var merge = function(nums1, m, nums2, n) {
            var i = m - 1,
                j = n - 1,
                index = m + n -1;
            while (i >= 0 && j >= 0){
                nums1[index--] = nums1[i] > nums2[j] ? nums1[i--] : nums2[j--];
            }
            while ( j >= 0){
                nums1[index--] = nums2[j--];
            }
};
```
### 时间

59 / 59 test cases passed.

Status: Accepted

Runtime: 60 ms

Your runtime beats 90.78 % of javascript submissions.
