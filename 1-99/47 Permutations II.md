[Permutations II](https://leetcode.com/problems/permutations-ii/description/)

### 问题描述
Given a collection of numbers that might contain duplicates, return all possible unique permutations.
```
For example,
[1,1,2] have the following unique permutations:
[
  [1,1,2],
  [1,2,1],
  [2,1,1]
]
```
### 问题解法
1. 与46题类型，只不过这一题加入了重复的条件。为了时间上的优化，这里我们采取46的方案二，用DFS实现
2. 大致思路几乎一模一样，只不过需要多加一点约束条件，将“已经使用过的元素不能重复使用”更正为“已经使用过的，包括与之相等的元素，均不能重复使用”
3. 因此当i不为0，i与i-1表示的数相等，且i-1没有被访问过的时候，说明这两个数深度相同，我们选谁都一样，因此为了避免重复，直接跳出当次循环，什么也不做。
> 如果i和前一个数相等，且前一个数被访问过了，说明这两个数处在不同的深度中，因此可以执行后续循环


### 源码
```
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
var permuteUnique = function(nums) {
        var res = new Array(),
            visited = new Array(),
            tmp = new Array();
        nums.sort();
        dfs(res,visited,nums,tmp);
        return res;
};
var dfs = function(res,visited,nums,tmp){
        if (tmp.length === nums.length){
            res.push(tmp.slice());
        }else{
            for (var i = 0; i < nums.length; i++){
                if (i !== 0 && nums[i] === nums[i-1] && !visited[i-1]) continue;
                if (!visited[i]){
                    visited[i] = true;
                    tmp.push(nums[i]);
                    dfs(res,visited,nums,tmp);
                    tmp.pop(tmp[tmp.length-1]);
                    visited[i] = false;
                }
            }
        }
};

```
### 运行时间

30 / 30 test cases passed.

Status: Accepted

Runtime: 80 ms

Your runtime beats 99.19 % of javascript submissions.
