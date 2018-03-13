[Container With Most Water](https://leetcode.com/problems/container-with-most-water/description/)
### 问题描述
Given n non-negative integers a1, a2, ..., an, where each represents a point at coordinate (i, ai). n vertical lines are drawn such that the two endpoints of line i is at (i, ai) and (i, 0). Find two lines, which together with x-axis forms a container, such that the container contains the most water.

Note: You may not slant the container and n is at least 2.
### 解法
1. 分情况讨论，然后遍历求最大值即可。最简单的做法当然是双重循环遍历，但并不推荐这样做。
2. 为了简化情况，首先假设底边最大 = right - left，这时最大值取决于两边中较短的那一边
3. 然后每次移动较短的那条边，遍历整个数组直到左右指针相遇，中间必定会找到一个MaxArea，这样只需要完整遍历一次数组即可。

> 怎么想到这种解法的？还是搜索的思路，即寻找问题的**初始条件**、**约束条件**、**最终目的值**
- 初始条件：任意两边加上底边，但这样存在两个变量，所以我们假设先从底边最大开始，作为初始条件
- 约束条件：即面积的Max
- 最终目的：整个数组的Max
> 这样思路就很明显了。遇到这样需要搜索、遍历的问题都可以用这样的方式来思考。
### 源码
```
/**
 * @param {number[]} height
 * @return {number}
 */
var maxArea = function(height) {
        var left = 0,
            right = height.length-1,
            maxres = 0;
        while (left < right){
            var long = right - left;
            maxres = Math.max(maxres, Math.min((height[left] * long), (height[right] * long)));
            if (height[left] < height[right]){
                left++;
            }else {
                right--;
            }
        }
        return maxres;
};
```
### 时间

49 / 49 test cases passed.

Status: Accepted

Runtime: 68 ms

Your runtime beats 100.00 % of javascript submissions.
