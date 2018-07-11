# 问题
[CLICK ME](https://leetcode.com/problems/baseball-game/description/)

# 解法
1. 本题实质就是按条件判断，并求一组连续值的和，这里用一个数组来存储比较合适【选择正确且优雅的数据结构是关键】

2. 然后根据条件来判断：
- C：数组内最后一个元素出栈，使用pop方法
- D：数组进栈一个元素，该元素是数组最后一个元素的2倍
- +：数组进栈一个元素，该元素是数组的倒数两个元素的和
- 数字：直接进栈，注意使用Number方法将字符串转换为数字

3. 最后累计求和
# 代码
```
/**
 * @param {string[]} ops
 * @return {number}
 */
var calPoints = function(ops) {
    var tmp = []
    var res = 0
    for (var i in ops) {
        if (ops[i] == 'C') {
            tmp.pop()
        }else if(ops[i] == 'D') {
            tmp.push(2 * tmp[tmp.length-1])
        }else if(ops[i] == '+') {
            tmp.push(tmp[tmp.length-1] + tmp[tmp.length-2])
        }else {
            tmp.push(Number(ops[i]))
        }
    }
    tmp.forEach((val, index) => {
        res += val
    })
    return res
};
```
