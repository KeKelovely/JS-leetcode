[Move Zeroes](https://leetcode.com/problems/move-zeroes/description/)
### 问题描述
Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements.

For example, given nums = [0, 1, 0, 3, 12], after calling your function, nums should be [1, 3, 12, 0, 0].

Note:
You must do this in-place without making a copy of the array.
Minimize the total number of operations.

### 解法描述
1. 移除掉数组中所有的0，并且不能有额外的空间消耗。这里如果就是在原数组上进行操作，可以发现我们要求的就是把所有的非0数按照原来的位置“挤到前排去”，
2. 于是，最简单的做法是直接进行赋值，遇到非0数就直接从数组第一位开始赋值，剩下的空间则依次赋值为0，就能实现我们想要的效果。

### 源码描述
```
/**
 * @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var moveZeroes = function(nums) {
    var insertPos = 0;
    for (var i = 0; i < nums.length; i++){
    	if (nums[i] !== 0){
    		nums[insertPos++] = nums[i];
    	}
    }
    for (var j = insertPos; j < nums.length; j++){
    		nums[j] = 0;
    }
};
```
