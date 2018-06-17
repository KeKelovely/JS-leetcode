# 问题
[click me](https://leetcode.com/problems/distribute-candies/description/)
# 解法
1. 本题需要将一堆糖果均分给姐姐和弟弟，要求分给姐姐的糖果数应尽可能大，并求出最大值
2. 这里无非就是一个次数统计，使用hash table来实现
3. 然后我们进行一个判断，哈希表的长度是否小于整个数组元素的一半（因为是均分），如果小于，说明哈希表内元素只有那么多，哈希表的长度就是糖果的种类
4. 如果大于，说明哈希表内糖果种类很多，那么返回数组元素的一半即可
5. 本质就是分类讨论，看哈希表的长度与数组元素一半的关系，分成不同的情况得到不同的糖果数
# 代码
```
/**
 * @param {number[]} candies
 * @return {number}
 */
var distributeCandies = function(candies) {
  var m = createHashTable(candies)
  return m.size < (candies.length / 2) ? m.size : candies.length / 2
};

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
