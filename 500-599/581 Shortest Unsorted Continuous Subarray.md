# 问题
[click me](https://leetcode.com/problems/shortest-unsorted-continuous-subarray/description/)
# 解法
1. 本题要求出一个最长的未经排序的子数组，将该子数组排序以后，整个数组都将变为有序序列
2. 这里的做法首先就是将数组排序，然后进行比较，记录第一个位置不相符的元素为start，就是我们所求的，然后一直向后遍历，直到求出最后一个元素的end位置
3. 最后end-start+1，就是我们所要的最大长度
# 代码
```
/**
 * @param {number[]} nums
 * @return {number}
 */
var findUnsortedSubarray = function(nums) {
  var arr = Array.from([...nums]).sort((a,b) => a-b)
  var start = -1
  var end = -2
  for (var i = 0; i < nums.length; i++) {
      if (nums[i] !== arr[i]) {
          if (start === -1) {
              start = i
          }
          end = i
      }
  }
  return end - start + 1
};
```
