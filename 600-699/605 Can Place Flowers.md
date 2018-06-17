# 问题
[Click me](https://leetcode.com/problems/can-place-flowers/description/)
# 解法
1. 本题要判断在给定数组的位置中是否可以种上足够数量的花，抽象成数学问题的本质就是看，是否存在符合要求的数组位置
2. 对数组位置的要求有：该位置的前后（[i-1], [i+1]）均不能为1
3. 在下面的做法中，首先将前一位置为0的情况全部算进去，然后再判断当后一位置的数为1时，前面那个数是否被填上了花（2），若是，则将结果减1
4. 其实就是分了两种情况来讨论前后位置不能为1的情形，因为花只能隔着种
# 代码
```
/**
 * @param {number[]} flowerbed
 * @param {number} n
 * @return {boolean}
 */
var canPlaceFlowers = function(flowerbed, n) {
    var res = 0
    for (var i in flowerbed) {
        if (flowerbed[i] == 0) {
            if (i == 0 || flowerbed[i-1] == 0) {
                flowerbed[i] = 2
                res++
            }
        }else {
            if (flowerbed[i-1] == 2) res--
        }
    }
    return n <= res
};
```
