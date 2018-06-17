# 问题
[Click me](https://leetcode.com/problems/maximum-product-of-three-numbers/description/)

# 解法
1. 本题要求出一个数组中三个数的乘积最大的结果（注意包括负数）
2. 这里最直观的操作就是首先用sort方法排序，最大乘积要么在最后三个元素（正数），要么是前两个元素和最后一个元素（含负数），比较求最大值即可
# 代码
```
/**
 * @param {number[]} nums
 * @return {number}
 */
var maximumProduct = function(nums) {
    nums.sort((a, b) => a-b)
    var len = nums.length
    return Math.max(nums[len-1] * nums[len-2] * nums[len-3], nums[0] * nums[1] * nums[len-1])
};
```
