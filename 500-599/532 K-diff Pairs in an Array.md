# 问题描述

[Click me](https://leetcode.com/problems/k-diff-pairs-in-an-array/description/)

# 解法

1. 本题的思路比较多，例如可以用哈希表（JS中的Map）来实现，首先我们将nums中的值作为index，val则是各index出现的次数，构建一个Map
2. 然后分类讨论。若k<0，直接返回0（因为题目要求的是绝对距离），若k=0，则我们只需要统计val不为1的次数（val不为1说明存在这样一个pairs，注意多个相同的pairs算1个），若k>0，我们只需要统计Map中是否存在val+k即可，使用map.has方法

# CODE
```
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number}
 */
var findPairs = function(nums, k) {
    var m = new Map(),
        count = 0;
    for (var i in nums) {
        if (m.has(nums[i])) {
            m.set(nums[i], m.get(nums[i])+1);
        }else {
            m.set(nums[i], 1);
        }
    }
    if (k == 0) {
        m.forEach((val,index) => {
            if (val != 1) {
                count++;
            }
        });
    }else if ( k > 0) {
        m.forEach((val,index) => {
            if (m.has(index+k)) {
                count++;
            }
        });
    }else if ( k < 0) {
        return count;
    }
    return count;
};
```
