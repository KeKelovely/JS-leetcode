# 问题

[Click me!](https://leetcode.com/problems/relative-ranks/description/)

# 解法

1. 找出数组中的前3个最大数并分别赋值G,S,B，其余的数从4,5,...开始计算
2. 先排序（这里需要先建立nums数组的一个复制，注意只能是值赋值，即不能var arr = nums,这样创建的是一个相同的引用，改变arr的同时也会改变nums），经试验
var arr = new Array(...nums)也不行，因为存在nums只有一个元素的情况，此时arr为空数组（这是扩展运算符的机制所限）,只能用循环遍历赋值
3. 然后就正常排序，使用一个Map结构，建立哈希表映射，如对数组[5,4,3,2,1]来说，Map {5=>'G',4=>'S',3=>'B',2=>'4',1=>'5'}
4. 最后取Map中的值并赋给nums即可
5. 总结：本题的关键在于如何建立GSB等值与原数组索引之间的映射，这里使用了Map（可以看成一种哈希表）来实现。排序是很简单的事情。

# Code
```
/**
 * @param {number[]} nums
 * @return {string[]}
 */
var findRelativeRanks = function(nums) {
    var arr = [],
        m = new Map();
    for (var k in nums){
        arr[k] = nums[k];
    }
    arr.sort((a,b)=>b-a);
    for (var i in arr){
        if (i == 0) {m.set(arr[i],'Gold Medal')}
        else if (i == 1) {m.set(arr[i],'Silver Medal')}
        else if (i == 2) {m.set(arr[i],'Bronze Medal')}
        else {m.set(arr[i],String(++i))}
    }
    for (var j in nums){
        nums[j] = m.get(nums[j]);
    }
    return nums;
};
```
