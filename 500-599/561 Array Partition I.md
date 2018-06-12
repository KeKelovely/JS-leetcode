# 问题描述

[Click me](https://leetcode.com/problems/array-partition-i/description/)

# 解法描述

# CODE
```
/**
 * @param {number[]} nums
 * @return {number}
 */
var arrayPairSum = function(nums) {
    var res = 0;
    nums.sort((a,b) => a-b);
    for (var i = 0; i < nums.length; i = i + 2) {
        res += nums[i];
    }
    return res;
};
```
