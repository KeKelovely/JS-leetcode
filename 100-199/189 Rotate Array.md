[Rotate Array](https://leetcode.com/problems/rotate-array/description/)

### 问题描述
Rotate an array of n elements to the right by k steps.

For example, with n = 7 and k = 3, the array [1,2,3,4,5,6,7] is rotated to [5,6,7,1,2,3,4].

Note:
Try to come up as many solutions as you can, there are at least 3 different ways to solve this problem.

### 解法描述
1. 往右将一个数组翻转k steps
2. 这里使用一个翻转的reverse_array()方法，然后依次用以下步骤完成翻转：（以问题描述中的example为例）
- 翻转整个数组，得到[7,6,5,4,3,2,1]
- 翻转前k个元素，得到[5,6,7,4,3,2,1]
- 翻转余下元素，得到[5,6,7,1,2,3,4]
3. 注意k值可能会大于nums.length，因此这里要取个余数
4. 之所以不用JavaScript自带的reverse方法，原因有二，第一个是自带的方法不支持翻转部分元素，第二个是效率不高，会带来额外的空间复杂度

### 源码
```
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var rotate = function(nums, k) {
    k = k % nums.length;
    reverse_array(nums,0,nums.length-1);
    reverse_array(nums,0,k-1);
    reverse_array(nums,k,nums.length-1);
};

var reverse_array = function(nums,left,right){
    while (left < right){
        [nums[left], nums[right]] = [nums[right], nums[left]];
        left++;
        right--;
    }
};
```

### 运行时间


33 / 33 test cases passed.

Status: Accepted

Runtime: 72 ms

Your runtime beats 95.78 % of javascript submissions.
