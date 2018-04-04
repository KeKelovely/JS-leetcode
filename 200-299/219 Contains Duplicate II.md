[Contains Duplicate II](https://leetcode.com/problems/contains-duplicate-ii/description/)
### 问题描述
Given an array of integers and an integer k, find out whether there are two distinct indices i and j in the array such that nums[i] = nums[j] and the absolute difference between i and j is at most k.

### 解法描述
1. 和217 Contains Duplicate 几乎一样的处理方法，还是使用JS的Map类型，只不过多了一个限制条件

### 源码描述
```
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {boolean}
 */
var containsNearbyDuplicate = function(nums, k) {
    var m = new Map();
    for (var i = 0; i < nums.length; i++){
        if (m.get(nums[i]) !== undefined && i - m.get(nums[i]) <= k){
            return true;
        }
        else {
            m.set(nums[i],i);
        }
    }
    return false;
};
```
