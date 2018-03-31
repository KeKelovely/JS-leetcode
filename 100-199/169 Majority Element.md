[Majority Element](https://leetcode.com/problems/majority-element/description/)

### 问题描述
Given an array of size n, find the majority element. The majority element is the element that appears more than ⌊ n/2 ⌋ times.

You may assume that the array is non-empty and the majority element always exist in the array.

### 解法描述
1. 找出数组中出现次数超过一半的元素，暴力遍历的方法自然不用多说，tricky一点的方法就是将数组排序，我们要找的元素一定是nums.length/2的元素
2. 分奇偶两种情况，画个图找规律就一目了然了，重点是利用好排序后数组的特点


### 源码
```
/**
 * @param {number[]} nums
 * @return {number}
 */
var majorityElement = function(nums) {
            nums.sort((a,b) => a-b);  
            var res = parseInt(nums.length / 2);
            return nums[res];
};
```

### 运行时间

44 / 44 test cases passed.

Status: Accepted

Runtime: 80 ms

Your runtime beats 67.91 % of javascript submissions.
