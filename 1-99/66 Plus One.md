[Plus One](https://leetcode.com/problems/plus-one/description/)
### 问题描述
Given a non-negative integer represented as a non-empty array of digits, plus one to the integer.

You may assume the integer do not contain any leading zero, except the number 0 itself.

The digits are stored such that the most significant digit is at the head of the list.
### 解法
1. 就是用一个链表来加1求结果。首先判断初始情况，如果为"1"，直接加1返回即可。
2. 然后从尾到头遍历：
- 该位上的数字不是9，那么直接加1，然后返回。直接break循环
- 该位上的数字是9，那么把9变为0
3. 最后，如果第一位也是0，说明需要进一位，在头部用unshift()方法加上一个1即可。

### 源代码实现
```
/**
 * @param {number[]} digits
 * @return {number[]}
 */
var plusOne = function(digits) {
        if (digits[0] === 0 && digits.length === 1){
            digits[0]++;
            return digits;
        }
        var i = digits.length - 1;
        while (i >= 0){
            if (digits[i] === 9){
                digits[i] = 0;
            }else {
                digits[i]++;
                break;
            }
            i--;
        }
        if (digits[0] === 0){
            digits.unshift(1);
        }
        return digits;
};
```

### 运行时间


108 / 108 test cases passed.

Status: Accepted

Runtime: 60 ms

Your runtime beats 85.56 % of javascript submissions.
