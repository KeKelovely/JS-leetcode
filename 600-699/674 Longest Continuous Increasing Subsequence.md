# 问题
[CLICK ME](https://leetcode.com/problems/longest-continuous-increasing-subsequence/description/)

# 解法
1. 本题要求出一个数组中连续的最长增长子序列，题目比较简单，从前往后逐个遍历，当遇到不满足条件的数时，令tmp为0（重新开始计数）
2. 最后注意考虑空数组的情形，以及要在最后的结果加上1（因为tmp只是对比较次数的统计，比如1 3 5，比较了两次，但实际上一共有3个数，所以加上1）

# 代码
```
/**
 * @param {number[]} nums
 * @return {number}
 */
var findLengthOfLCIS = function(nums) {
    var tmp = 0
    var longest = 0
    if (nums.length == 0) {
        return 0
    }
    for (var i = 1; i < nums.length; i++) {
        if (nums[i-1] < nums[i]) {
            tmp++
        }else {
            longest = Math.max(longest, tmp)
            tmp = 0
        }
        longest = Math.max(longest, tmp)
    }
    return longest+1
};
```
