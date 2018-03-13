# 1 Two Sum
[Two Sum](https://leetcode.com/problems/two-sum/description/)
### 问题描述
Given an array of integers, return indices of the two numbers such that they add up to a specific target.
You may assume that each input would have exactly one solution, and you may not use the same element twice.
### 思路
1. 最简单的做法就是遍历整个数组
2. 参考答案中为了优化遍历时间使用了HashTable，（二次 → 线性），代价是额外的空间消耗。
3. js没有原生的hashtable结构，需要自己构造。不过js中的object类型就是一个类似的结构，稍微包装一下即可实现。

```
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
        for (var i = 0; i < nums.length; i++){
            var j = nums.indexOf(target - nums[i]);
            if ( j !== i && j > -1){
                return [i,j];
            }
        }
};
```
### 运行时间
19 / 19 test cases passed.
Status: Accepted
Runtime: 180 ms
Your runtime beats 60.23 % of javascript submissions.
