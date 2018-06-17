# 问题
[Click me](https://leetcode.com/problems/minimum-index-sum-of-two-lists/description/)
# 解法
1. 本题的实质就是求出两个字符串数组中的index之和最小的公共元素，注意有两个条件，其一是公共元素，其二是index之和最小
2. 剩下的就是直接判断就好了，用一个变量来存储索引之和，如果小则存储到结果中去
3. 使用indexOf方法，若返回-1则说明不存在该元素
# 代码
```
/**
 * @param {string[]} list1
 * @param {string[]} list2
 * @return {string[]}
 */
var findRestaurant = function(list1, list2) {
    var res = []
    var indexSum = Number.MAX_VALUE
    for (var i = 0; i < list1.length; i++) {
        if (list2.indexOf(list1[i]) !== -1 && list2.indexOf(list1[i]) + i <= indexSum) {
            res.push(list1[i])
            indexSum = i + list2.indexOf(list1[i])
        }
    }
    return res
};
```
