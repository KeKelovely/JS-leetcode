# 问题描述
You are given two arrays (without duplicates) nums1 and nums2 where nums1’s elements are subset of nums2. Find all the next greater numbers for nums1's elements in the corresponding places of nums2.

The Next Greater Number of a number x in nums1 is the first greater number to its right in nums2. If it does not exist, output -1 for this number.

Example 1:
```
Input: nums1 = [4,1,2], nums2 = [1,3,4,2].
Output: [-1,3,-1]
Explanation:
    For number 4 in the first array, you cannot find the next greater number for it in the second array, so output -1.
    For number 1 in the first array, the next greater number for it in the second array is 3.
    For number 2 in the first array, there is no next greater number for it in the second array, so output -1.
```

Example 2:
```
Input: nums1 = [2,4], nums2 = [1,2,3,4].
Output: [3,-1]
Explanation:
    For number 2 in the first array, the next greater number for it in the second array is 3.
    For number 4 in the first array, there is no next greater number for it in the second array, so output -1.
```
Note:
All elements in nums1 and nums2 are unique.
The length of both nums1 and nums2 would not exceed 1000.

# 解法
1. 本题要求找出数组中所有的next greater number，具体的定义可参照上面的英文题干
2. 这里一种做法是暴力求解，使用Array.indexOf方法，遍历nums1，找出nums1中所有值在nums2的index，再遍历该index之后剩下的元素，看是否会找到greater number

# 代码一：
```
/**
 * @param {number[]} findNums
 * @param {number[]} nums
 * @return {number[]}
 */
var nextGreaterElement = function(findNums, nums) {
    var res = [];
    for (var i = 0; i < findNums.length; i++){
        var pos = nums.indexOf(findNums[i]);
        if (pos === nums.length-1){
            res.push(-1);
        }
        for (var j = pos+1; j < nums.length; j++){
            if (nums[pos] < nums[j]){
                res.push(nums[j]);
                break;
            }
            if (j === nums.length-1){
                res.push(-1);
            }
        }
    }
    return res;
};
```

3. 另一种解法比较巧妙，既然nums1是nums2的子集，那不如直接先求nums2中的所有greater number构成的一个哈希表，其中value即对应index的greater number
4. 这里需要使用到stack栈，将nums2中的元素依次入栈，再判断后入栈的元素是否大于前面的元素，if是，说明找到了更大的数，则前面元素出栈并建立映射
5. 相比前一种解法的复杂度O(m * n)，栈方法将复杂度变为O(m + n)，相比要好很多~
# 代码二

```
/**
 * @param {number[]} findNums
 * @param {number[]} nums
 * @return {number[]}
 */
var nextGreaterElement = function(findNums, nums) {
    var stack = [],
        m = new Map();
    for (var i in nums){
        while ( stack.length && stack[stack.length-1] < nums[i]){
            m.set(stack.pop(),nums[i]);
        }
        stack.push(nums[i]);
    }
    for (var j in findNums){
        if (m.has(findNums[j])) {
            findNums[j] = m.get(findNums[j]);
        }else{
            findNums[j] = -1;
        }
    }
    return findNums;
};
```
# 总结
- 涉及到数组中的**顺序**，**比较**等问题类型时，尝试用栈的数据结构，也许会有意外的收获~
