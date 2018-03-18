[Median of Two Sorted Arrays](https://leetcode.com/problems/median-of-two-sorted-arrays/description/)
### 问题描述
There are two sorted arrays nums1 and nums2 of size m and n respectively.

Find the median of the two sorted arrays. The overall run time complexity should be O(log (m+n)).

Example 1:

```
nums1 = [1, 3]
nums2 = [2]
The median is 2.0
```

Example 2:

```
nums1 = [1, 2]
nums2 = [3, 4]
The median is (2 + 3)/2 = 2.5
```
### 解法一
1. 如果不考虑问题给出的限制条件：The overall run time complexity should be O(log (m+n))，当然最简单的做法就是用Array类型的sort()方法，将合并后的
数组排序，然后分奇偶找出中位数即可。
2. 注意一个陷阱，JavaScript自带的sort()方法并不能对整数进行“正常排序”，因为sort()方法默认是按照字符编码顺序来排，所以10会被放在2前面，导致出错。为了解决
这一问题，需要我们手动传入compare()函数
### 源码实现
```
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number}
 */
var findMedianSortedArrays = function(nums1, nums2) {
            var nums3 = nums1.concat(nums2);
            nums3.sort(compare);
            var len = nums3.length;
            if (len % 2 === 1){
                return nums3[ (len-1)/2 ];
            }
            if (len % 2 === 0){
                return (nums3[ (len/2-1) ] + nums3[ len/2 ]) / 2;
            }
};
var compare = function(num1,num2){
            if (num1 < num2){
                return -1;
            }
            if (num1 > num2){
                return 1;
            }
}
```
### 运行时间

2080 / 2080 test cases passed.

Status: Accepted

Runtime: 164 ms

Your runtime beats 62.27 % of javascript submissions.
