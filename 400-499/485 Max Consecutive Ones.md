# 问题描述

Given a binary array, find the maximum number of consecutive 1s in this array.

Example 1:
```
Input: [1,1,0,1,1,1]
Output: 3
Explanation: The first two digits or the last three digits are consecutive 1s.
    The maximum number of consecutive 1s is 3.
```
Note:

The input array will only contain 0 and 1.
The length of input array is a positive integer and will not exceed 10,000

# 解法
1. 问题是求一个只含有0和1的数组中全部为1的最长子序列，如[1,1,0,1,1,1]的全为1的最长子序列为[1,1,1]，长度即为3
2. 比较简单的一题，直接遍历整个数组，每次记录下max值，当遇到0时，count归0即可。

# 代码
```
/**
 * @param {number[]} nums
 * @return {number}
 */
var findMaxConsecutiveOnes = function(nums) {
    var count = 0,
        max = 0;
    for (var i = 0; i < nums.length; i++){
        if (nums[i]){
            count++;
        }else if (!nums[i]){
            count = 0;
        }
        max = Math.max(max,count);
    }
    return max;
};
```
