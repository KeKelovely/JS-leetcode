# 问题描述
You are given a map in form of a two-dimensional integer grid where 1 represents land and 0 represents water. Grid cells are connected horizontally/vertically (not diagonally). The grid is completely surrounded by water, and there is exactly one island (i.e., one or more connected land cells). The island doesn't have "lakes" (water inside that isn't connected to the water around the island). One cell is a square with side length 1. The grid is rectangular, width and height don't exceed 100. Determine the perimeter of the island.

Example:
```
[[0,1,0,0],
 [1,1,1,0],
 [0,1,0,0],
 [1,1,0,0]]
```
Answer: 16
Explanation: The perimeter is the 16 yellow stripes in the image below:

![pic](https://leetcode.com/static/images/problemset/island.png)

# 解法

1. 一个小岛被海水包围，每边长为1，求图中小岛的边长
2. 这里可以直接求解，也可以反向求解。这里主要讨论反向求解方法，即先暴力统计所有小岛中正方形的边数，即个数*4(注意每条边重复算了两次)
3. 然后求重叠的边，由于重复计算，求出的结果需要*2。
4. 剩下的问题就是求重叠边，依次统计每个矩形的“左上”边，看是否有1即可，有1则重复边加1

# 代码
```
/**
 * @param {number[][]} grid
 * @return {number}
 */
var islandPerimeter = function(grid) {
    var m = grid.length,
        n = grid[0].length,
        edge = 0,
        repeat = 0;
    for (var i = 0; i < m; i++){
        for (var j = 0; j < n; j++){
            if (grid[i][j]){
                edge++;
                (i!==0)&&(grid[i-1][j])&&(repeat++);
                (j!==0)&&(grid[i][j-1])&&(repeat++);
            }
        }
    }
    return edge * 4 - repeat * 2;
};
```
