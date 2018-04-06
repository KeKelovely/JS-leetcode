[Range Sum Query - Immutable](https://leetcode.com/problems/range-sum-query-immutable/description/)

### 问题描述
Given an integer array nums, find the sum of the elements between indices i and j (i ≤ j), inclusive.

Example:
```
Given nums = [-2, 0, 3, -5, 2, -1]

sumRange(0, 2) -> 1
sumRange(2, 5) -> -1
sumRange(0, 5) -> -3
```
Note:
You may assume that the array does not change.
There are many calls to sumRange function.

### 解法描述
1. 用一个数组来保存每位累计之和，然后再求指定区间内的和即可，比较简单
2. 本题要用OOP的写法，注意用this.nums指定nums，防止方法内指向的对象不明，否则会一直报错显示nums未定义

### 源码
```
/**
 * @param {number[]} nums
 */

var NumArray = function(nums) {
    this.nums = nums;
    for (let i = 1; i < nums.length; i++){
        this.nums[i] += this.nums[i-1];
    }
};

/** 
 * @param {number} i 
 * @param {number} j
 * @return {number}
 */
NumArray.prototype.sumRange = function(i, j) {
    if (i === 0)   return this.nums[j];
    return this.nums[j] - this.nums[i-1];
};

/** 
 * Your NumArray object will be instantiated and called as such:
 * var obj = Object.create(NumArray).createNew(nums)
 * var param_1 = obj.sumRange(i,j)
 */
```
