[Permutations](https://leetcode.com/problems/permutations/description/)
### 问题描述
Given a collection of distinct numbers, return all possible permutations.
```
For example,
[1,2,3] have the following permutations:
[
  [1,2,3],
  [1,3,2],
  [2,1,3],
  [2,3,1],
  [3,1,2],
  [3,2,1]
]
```

### 问题解法
1. 全排列问题，[讲解请戳这里](https://www.youtube.com/watch?v=1Taz3r2mB5U)
### 解法一
1. 暴力递归。以题目的初始例子为例，先固定元素“1”，然后进行全排列，得到“1,2,3”和“1,3,2”（这一过程通过递归实现）
2. 然后将数组第一个元素“1”与第二个元素“2”交换，重复上述操作，得到“2,1,3”和“2,3,1”
3. 最后得到“3,1,2”和“3,2,1”
- 总结：每次固定第一个元素，然后进行全排列，找出所有情况。
- 这种解法也就是对手工写全排列思路的一个模仿，代价是会用到多次递归，**效率低**，但思路很好理解

### 源码实现
```
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
var permute = function(nums) {
        var target = [];
        permutation(nums,0,nums.length,target);
        return target;
};
        var permutation = function(numbers,left,right,target){
            if (left === right){
                target.push(numbers.slice());
            }else {
                for (var i = left; i < right; i++){
                    [numbers[i],numbers[left]] = [numbers[left],numbers[i]]; 
                    permutation(numbers,left+1,right,target);
                    [numbers[i],numbers[left]] = [numbers[left],numbers[i]];
                }
            }
        };
```
### 运行时间

25 / 25 test cases passed.

Status: Accepted

Runtime: 112 ms

Your runtime beats 44.55 % of javascript submissions.

### 解法二
1. backtrack，或者说就是之前提过的回溯/搜索的思路（深度优先遍历），照例基本操作：
- 初始条件：原始数组1,2,3
- 约束条件：打乱顺序排列，要求是已经使用过的元素不允许再用，每个元素只允许插入一次
- 目标条件：找出所有的元素组合
2. 这里用到一个额外的空间tmp[i]来存储数组元素，并用一个visited[i]数组来存放元素是否被用过的布尔值
- 即，遍历整个数组
- 将数组的第一个元素放入到tmp[0],visited[0]=true，表示1已经被使用过了
- 对后续元素进行类似操作（递归），找出所有结果“123”“132”
- 找到数组的第二个元素，重复上述操作。
3. 这种解法的代价是会付出额外的空间消耗，但是运行时间会有明显的优化（减少了递归的次数）
> 这个解法看起来不太直观，但思路是差不多的，主要是要能联想到用一个额外的数组来存储，并考虑到约束条件：每个元素只能用到一次

### 源码实现
```
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
var permute = function(nums) {
        var result = [],
            visited = [],
            tmp = [];
        nums.sort();
        dfs(result,visited,nums,tmp);
        return result;
};
var dfs = function(result,visited,nums,tmp){
        if (tmp.length === nums.length){
            result.push(tmp.slice());
        }else{
            for (var i = 0, imax = nums.length; i < imax; i++){
                if (!visited[i]){
                    visited[i] = true;
                    tmp.push(nums[i]);
                    dfs(result,visited,nums,tmp);
                    tmp.pop();
                    visited[i] = false;
                }
            }
        }
};
```
### 运行时间
25 / 25 test cases passed.

Status: Accepted

Runtime: 72 ms

Your runtime beats 94.87 % of javascript submissions.
