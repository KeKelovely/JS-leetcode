[Maximum Subarray](https://leetcode.com/problems/maximum-subarray/description/)
### 问题描述
Find the contiguous subarray within an array (containing at least one number) which has the largest sum.

For example, given the array [-2,1,-3,4,-1,2,1,-5,4],
the contiguous subarray [4,-1,2,1] has the largest sum = 6.

### 解法一：
1. 从算法的角度来说，最普适的解法就是"Divide and Conquer"，简单来说，将情况分成三种：
- max位于整个数组的左半部分，遍历整个数组找出最大值，用递归实现
- max位于整个数组的右半部分，同上
- max位于数组的中间（左右都有），那么首先分别求出左半数组的最大值（包括左半数组的最后一个值），再求出右半数组的最大值（包括右半数组的第一个值）。
最后将两个值相加，即可得到max
- 最后在通过这三种方法求出来的max中进行比较，所找出的最大值就是整个数组的最大值（因为整个数组的max只可能出现在这三种情况中。）

### 解法二：
1. 本题可以取巧来做，首先从数组的第一个元素开始找起，令其为thissum和maxsum，thissum表示当前的累计和
2. 从第二个元素nums[1]开始遍历之，如果thissum小于0，那么直接取当前元素nums[i]作为thissum。
> 换言之，如果在遍历中，我们找出的数组和变成了负数，那么这个数组和一定不会是最大值（可以用反证法）
3. 如果thissum大于0，那么在thissum的基础上加上当前元素nums[i]，再判断thissum是否大于maxsum，赋值即可

### 源码实现
```
/**
 * @param {number[]} nums
 * @return {number}
 */
var maxSubArray = function(nums) {
            var len = nums.length;
            if (len === 0){
                return 0;
            }
            if (len === 1){
                return nums[0];
            }
            var thissum = nums[0],
                maxsum = nums[0];
            for (var i = 1; i < len; i++){
                if (thissum < 0){
                    thissum = nums[i];
                }else{
                    thissum += nums[i];
                }
                if (thissum > maxsum)
                    maxsum = thissum;
            }
            return maxsum;
};
```
### 运行时间

202 / 202 test cases passed.

Status: Accepted

Runtime: 64 ms

Your runtime beats 93.78 % of javascript submissions.
