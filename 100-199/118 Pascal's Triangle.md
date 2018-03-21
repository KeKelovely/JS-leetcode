[Pascal's Triangle](https://leetcode.com/problems/pascals-triangle/description/)
### 问题描述
Given numRows, generate the first numRows of Pascal's triangle.

For example, given numRows = 5,
Return
```
[
     [1],
    [1,1],
   [1,2,1],
  [1,3,3,1],
 [1,4,6,4,1]
]
```

### 解法：迭代实现
1. 按顺序来即可，每次循环创建一个数组tmp，特点是tmp的首尾元素一定是1（观察上面的规律可知）
2. tmp除首尾元素外的中间元素，满足上一个数组的前两位之和，嘛，就是个数学trick，规律性的东西
3. 每次将tmp放入res数组中，最后得到的res就是我们要的目标输出
### 源码
```
/**
 * @param {number} numRows
 * @return {number[][]}
 */
var generate = function(numRows) {
            var res = [];
            if (numRows === 0){
                return res;
            }
            for (var i = 0; i < numRows; i++){
                var tmp = [];
                tmp.length = i+1;
                tmp[0] = 1, tmp[i] = 1;
                for (var j = 1; j < i; j++){
                    tmp[j] = res[i-1][j-1] + res[i-1][j];
                }
            res.push(tmp);
            }
            return res;
};
```

### 运行时间

15 / 15 test cases passed.

Status: Accepted

Runtime: 60 ms

Your runtime beats 79.91 % of javascript submissions.
