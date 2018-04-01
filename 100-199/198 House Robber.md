[House Robber](https://leetcode.com/problems/house-robber/description/)
### 问题描述
You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security system connected and it will automatically contact the police if two adjacent houses were broken into on the same night.

Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight without alerting the police.

### 解法描述
1. 意思就是说，求一个数组中任意两个不相邻元素之和的最大值。这是一个典型的DP问题，即全局最优解一定是建立在局部最优解的基础之上。
2. 换言之，假设d[i]表示前i个数中我们所求的最大值，那么d[i]一定和d[i-n]有关，具体说就是：
对当前第i个房子而言，有两种情况，rob or not rob：
- rob： d[i] = d[i-2] + nums[i]
- not rob: d[i] = d[i-1]
> d[i]的最优解一定是基于d[i-1]和d[i-2]的
3. 剩下就是分别求最大值，遍历数组的基本操作

### 源码实现
```
/**
 * @param {number[]} nums
 * @return {number}
 */
var rob = function(nums) {
    var sum = [];
    if (nums.length === 0){
        return 0;
    }
    sum[0] = nums[0];
    sum[1] = Math.max(nums[0], nums[1]);
    for (var i = 2; i < nums.length; i++){
        sum[i] = Math.max(sum[i-2] + nums[i], sum[i-1]);
    }
    return sum[nums.length-1];
};
```

### 运行时间

69 / 69 test cases passed.

Status: Accepted

Runtime: 60 ms

Your runtime beats 69.83 % of javascript submissions.
