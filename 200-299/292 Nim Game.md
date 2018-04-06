[Nim Game](https://leetcode.com/problems/nim-game/description/)

### 问题描述
You are playing the following Nim Game with your friend: There is a heap of stones on the table, each time one of you take turns to remove 1 to 3 stones. The one who removes the last stone will be the winner. You will take the first turn to remove the stones.

Both of you are very clever and have optimal strategies for the game. Write a function to determine whether you can win the game given the number of stones in the heap.

For example, if there are 4 stones in the heap, then you will never win the game: no matter 1, 2, or 3 stones you remove, the last stone will always be removed by your friend.

### 解法描述
1. 还是个奥数题..正如题目所说，如果n = 4，那么player就是必输的局面。如果n = 5/6/7，那么player总能赢（因为player一定可以给对手留下4个stones）
2. 同理如果n = 8， 那么player怎么都是个死，所以我们就猜测，只要n是4的倍数，那么player就是必输的局面
3. 严格的证明可以使用数学归纳法

### 源码
```
/**
 * @param {number} n
 * @return {boolean}
 */
var canWinNim = function(n) {
        return (n % 4 !== 0);
};
```
