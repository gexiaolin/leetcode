# 65. 最小路径和

+ 题目地址：[leetcode](https://leetcode-cn.com/problems/minimum-path-sum/)
+ 题目难度：medium

## 思路

动态规划，记录到达当前坐标 `x, y` 的最小值，仅需对比 `x - 1, y` 和 `x, y - 1` 中的较小值并存储（此处直接覆盖grid对应坐标即可，无需额外开销）。

时间复杂度O(mn)

空间复杂度O(1)

## 解答

```js
/**
 * @param {number[][]} grid
 * @return {number}
 */
var minPathSum = function(grid) {
    // 考虑边界情况
    if (!grid.length) return 0;

    // 获取x轴和y轴长度
    let lenX = grid[0].length;
    let lenY = grid.length;

    for (let i = 0; i < lenY; i++) {
        for (let j = 0; j < lenX; j++) {
            if (i === 0 && j === 0) continue;

            let currentNum = grid[i][j];
            if (i === 0) {
                grid[i][j] = currentNum + grid[i][j - 1];
            } else if (j === 0) {
                grid[i][j] = currentNum + grid[i - 1][j];
            } else {
                grid[i][j] = currentNum + Math.min(grid[i - 1][j], grid[i][j - 1]);
            }
        }
    }
    
    return grid[lenY - 1][lenX - 1];
};
```

## 性能

执行用时 : 64 ms , 在所有 JavaScript 提交中击败了 92.24% 的用户

内存消耗 : 35.8 MB , 在所有 JavaScript 提交中击败了 68.18% 的用户
