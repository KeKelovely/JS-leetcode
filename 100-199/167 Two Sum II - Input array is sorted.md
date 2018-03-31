[Two Sum II - Input array is sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/)

### 问题描述
Given an array of integers that is already sorted in ascending order, find two numbers such that they add up to a specific target number.

The function twoSum should return indices of the two numbers such that they add up to the target, where index1 must be less than index2. Please note that your returned answers (both index1 and index2) are not zero-based.

You may assume that each input would have exactly one solution and you may not use the same element twice.

Input: numbers={2, 7, 11, 15}, target=9
Output: index1=1, index2=2

### 解法描述
1. 给出一个已经排序好的数组，找出其中两个元素之和等于target的元素，并以数组的形式返回这两个元素的下标
2. 例如input为numbers={2, 7, 11, 15}, target=9，output应该是[1,2]
3. 用左右两个指针（更准确地说应该是数组头尾的两个指针）向数组中间遍历，由于数组已经排好序，如果两数之和大于target，那么应当让
两数之和“变小”，显然就让右边的指针往左边跑，同理如果小于target，让左边的指针往右边跑
### 源码
```
/**
 * @param {number[]} numbers
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(numbers, target) {
            var nums = new Array();
            if (numbers.length < 2 || numbers === null){
                return nums;
            }
            var left = 0,
                right = numbers.length - 1;
            while (left < right){
                plus = numbers[left]+numbers[right];
                if (plus === target){
                    left++;
                    right++;
                    nums = [left,right];
                    return nums;
                }else if (plus < target){
                    left++;
                }else if (plus > target){
                    right--;
                }
            }
};
```
### 运行时间

16 / 16 test cases passed.

Status: Accepted

Runtime: 64 ms

Your runtime beats 82.65 % of javascript submissions.

