[Remove Element](https://leetcode.com/problems/remove-element/description/)
### 问题描述
Given an array and a value, remove all instances of that value in-place and return the new length.

Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.

The order of elements can be changed. It doesn't matter what you leave beyond the new length.
```
Example:

Given nums = [3,2,2,3], val = 3,

Your function should return length = 2, with the first two elements of nums being 2.
```
### 解法：
1. 和#26几乎一模一样的思路，同样是考虑双指针的实现，注意指针的起始位置

> 使用双指针的目的是为了减少空间复杂度（不让你使用额外的数组），当然这也会增加代码复杂度

### 源码
```
/**
 * @param {number[]} nums
 * @param {number} val
 * @return {number}
 */
var removeElement = function(nums, val) {
            var pos = 0;
            for (var i = 0; i < nums.length; i++){
                if ( nums[i] !== val ){
                    nums[pos++] = nums[i];
                }
            }
        return pos;
};
```
### 运行时间

113 / 113 test cases passed.

Status: Accepted

Runtime: 64 ms

Your runtime beats 100.00 % of javascript submissions.
