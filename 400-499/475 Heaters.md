# 问题描述

[Click me!](https://leetcode.com/problems/heaters/description/)

# 解法

1. 本题的关键在于找出houses两侧最近的heaters所在的位置，然后比较前后heaters与houses的距离，取min即为所求（找到距离houses的位置最近的heaters，就是我们要求的结果）。最后我们需要在所有的加热半径中找到最大值。
2. 这里为了找到最近的heaters所在的位置，既可以暴力遍历，不过也可以使用Binary Search的方法，简化搜索流程。
3. 注意当right == 0时，说明此时heaters位于最左边（相当于不存在上一个heaters啦），只需要求一边的距离即可。

# Code
```
/**
 * @param {number[]} houses
 * @param {number[]} heaters
 * @return {number}
 */
var findRadius = function(houses, heaters) {
    var max = 0;
    houses.sort((a,b)=>a-b);
    heaters.sort((a,b)=>a-b);
    for (var i in houses){
        var left = 0,
            right = heaters.length - 1;
        while (left < right){
            var mid = left + parseInt((right - left)/2);
            if (houses[i] > heaters[mid]){
                left = mid + 1;
            }else{
                right = mid;
            }
        }
        if (right == 0){
            max = Math.max(max, Math.abs(heaters[right] - houses[i]));
        }else {
            var dis1 = Math.abs(heaters[right] - houses[i]);
            var dis2 = Math.abs(houses[i] - heaters[right-1]);
            max = Math.max(max, Math.min(dis1,dis2));
        }
    }
    return max;
};
```
