# 问题
[click me](https://leetcode.com/problems/longest-harmonious-subsequence/description/)
# 解法
1. 本题要求出一个最长的子序列的长度，要求是这个最长子序列只能包含两个相差为1的数字
2. 既然本题涉及到统计元素个数，当然直接用一个Hash Table来记录数组中元素出现次数就好了，然后我们使用forEach方法遍历哈希表，找出所有满足条件的结果，并比较求得最大值
# 代码
```
/**
 * @param {number[]} nums
 * @return {number}
 */
var findLHS = function(nums) {
  var m = createHashTable(nums)
  var max = 0
  m.forEach((val, index) => {
    if (m.has(index+1)) {
      max = Math.max(max, m.get(index) + m.get(index+1))
    }
  })
  return max
}

var createHashTable = function(nums) {
  var m = new Map()
  for (var i in nums) {
  	if (m.has(nums[i])) {
  		m.set(nums[i], m.get(nums[i])+1)
  	}else {
  		m.set(nums[i], 1)
  	}
  }
  return m
}
```
