# 问题
[Click me!](https://leetcode.com/problems/maximum-average-subarray-i/description/)

# 解法
1. 本题要求出目标数组中给定长度的子数组的最大平均值，简而言之，找出长度为k的子数组，要求其平均值为最大（也就是和最大，因为k是固定的）
2. 这里可以遍历一遍数组即可（O(n)复杂度），首先求出前k个之和，然后每次将子数组向右移动一位（加上最右边的一个数，减去最左边的一个数），比较后找出最大值
3. 最后将结果除以k，即为所求的最大值

# 代码
```
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number}
 */
var findMaxAverage = function(nums, k) {
    var sum = 0
    for (var i = 0; i < k; i++) {
        sum += nums[i]
    }
    var res = sum
    for (var j = k; j < nums.length; j++) {
        sum += nums[j] - nums[j-k]
        res = Math.max(res, sum)
    }
    return res/k
};
```
