# 问题
[Click me](https://leetcode.com/problems/set-mismatch/description/)

# 解法
1. 仔细阅读题意！本题是说在一个数组中，有一个数取代了另一个数的位置，换言之，有一个数a重复出现了2次，有一个数b没有出现，且这个数组由1~n的整数构成
2. 问题就在于如何找出。这里由于数组是由1~n的整数构成，取巧的方法是将数组值作为数组的下标来使用
3. 如果一个数存在，那么对应下标的数组值我们让它乘以-1变成负数，如此循环，可以得到三种情况：
- 如果一个数只出现1次，其作为下标时，对应数组值为负数
- 如果一个数出现2次，其作为下标时，对应的数组值应为正数（因为乘了两次-1），这时对应的下标+1就是我们所求的结果
- 如果一个数没有出现，其作为下标时，对应数组值也为正数（因为压根就没乘-1），这时同样结果就是对应的下标+1

情况1、2对应第一个for循环的逻辑
情况3对应第二个for循环的逻辑，见下面代码

# 代码
```
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var findErrorNums = function(nums) {
    var res = []
    for (var i = 0; i < nums.length; i++) {
        var index = Math.abs(nums[i]) - 1
        if (nums[index] > 0) {
            nums[index] *= -1
        }else {
            res.push(index + 1)
        }
    }
    for (var j = 0; j < nums.length; j++) {
        if (nums[j] > 0) {
            res.push(j + 1)
        }
    }
    return res
};
```
