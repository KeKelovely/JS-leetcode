[Contains Duplicate](https://leetcode.com/problems/contains-duplicate/description/)
### 问题描述
Given an array of integers, find if the array contains any duplicates. Your function should return true if any value appears at least twice in the array, and it should return false if every element is distinct.

### 解法描述
1. 找出数组中成对的元素，这里较方便的做法是采用JS的Map类型，将数组的每一个元素作为一个“键”，然后赋予相应的值（我们只需要键就行了，具体映射的值是多少其实无所谓）
2. 然后使用Map类型的has()方法，如果当前键值已经存在于Map中，那么has()方法就会返回true，说明这就是我们要找的重复元素。

### 源码描述
```
/**
 * @param {number[]} nums
 * @return {boolean}
 */
var containsDuplicate = function(nums) {
    var m = new Map();
    for (var i = 0; i < nums.length; i++){
        if (m.get(nums[i]) !== undefined){
            return true;
            break;
        }
        m.set(nums[i],i); 
    }
    return false;
};
```
