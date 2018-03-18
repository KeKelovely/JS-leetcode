[Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/)
### 问题描述：
Given a sorted array, remove the duplicates in-place such that each element appear only once and return the new length.

Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.
```
Example:

Given nums = [1,1,2],
```
Your function should return length = 2, with the first two elements of nums being 1 and 2 respectively.
It doesn't matter what you leave beyond the new length.
### 解法：
1. **去除掉**数组中的重复元素
- 注意正确理解题意，由于题设限制，这里并不是真的删除了数组元素，而是通过构造指针的方式间接实现，**只输出非重复的元素**
2. 问题解法：构造双指针，第一个指针用来遍历整个数组，第二个指针用来指向合乎题意的数据，若元素不等，则将元素放入第二个指针指向的**伪数组**中，然后使第二个指针+1，转向下一位置

> 本题思路很简单，重点是对于双指针的理解，尤其是指针起始位置的选择，要在脑海中建构一个形象的结构

### 源码：
```
/**
 * @param {number[]} nums
 * @return {number}
 */
var removeDuplicates = function(nums) {
        var pos = 1;
        var s = nums[0];
        if (nums.length === 0){
            return nums;
        }
        for (var i = 1; i < nums.length; i++){
            if (nums[i] !== s){
                nums[pos++] = nums[i];
                s = nums[i];
            }
        }
        return pos;
};
```
### 运行时间

161 / 161 test cases passed.

Status: Accepted

Runtime: 72 ms

Your runtime beats 100.00 % of javascript submissions.
