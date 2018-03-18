[Search Insert Position](https://leetcode.com/problems/search-insert-position/description/)

### 问题描述

### 解法

1. 这里实际上就是Binary Search的应用（当然你可以暴力遍历整个数组233）
2. 由于题目限制，这里并不能使用indexOf()方法，本来最好也不要使用，因为本题的意义就在于考查二分查找
3. **务必熟悉二分查找的源码实现**（是迭代不是递归！！）

### 源码
```
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var searchInsert = function(nums, target) {
        var left = 0,
            right = nums.length-1;
        while (left <= right){
            var mid = parseInt( (left + right) / 2 );
            if (nums[mid] === target){
                return mid;
                break;
            }else if (nums[mid] > target) {
                right = mid - 1;
            }else if (nums[mid] < target){
                left = mid + 1;
            }
        }
        if (left > right){
            return right+1;
        }
};
```
### 运行时间

62 / 62 test cases passed.

Status: Accepted

Runtime: 60 ms

Your runtime beats 100.00 % of javascript submissions
