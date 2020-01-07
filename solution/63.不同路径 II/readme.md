# 63. 不同路径 II

+ 题目地址：[leetcode](https://leetcode-cn.com/problems/unique-paths-ii/)
+ 题目难度：medium

## 思路

动态规划，拆解答案，思路与62题基本一致，只需要额外考虑 `x, y` 坐标为1的情况，此时该坐标格子走不通，路径数记为0。

## 答案

```js
/**
 * @param {number[][]} obstacleGrid
 * @return {number}
 */
var uniquePathsWithObstacles = function(obstacleGrid) {
    // 判断边界情况
    if (!obstacleGrid.length) return 0;
    if (obstacleGrid.length && obstacleGrid[0][0] === 1) return 0;

    // 获取x轴和y轴长度
    let lenX = obstacleGrid[0].length;
    let lenY = obstacleGrid.length;

    let map = {};

    for (let i = 0; i < lenY; i++) {
        map[i] = {};

        for (let j = 0; j < lenX; j++) {
            if (i === 0 && j === 0) {
                map[i][j] = 1;
                continue;
            }
            if (obstacleGrid[i][j] === 1) {
                map[i][j] = 0;
                continue;
            }

            if (i === 0) {
                map[i][j] = map[i][j - 1];
            } else if (j === 0) {
                map[i][j] = map[i - 1][j];
            } else {
                map[i][j] = map[i][j - 1] + map[i - 1][j];
            }
        }
    }
    
    return map[lenY - 1][lenX - 1];
};
```

## 性能

执行用时 : 68 ms , 在所有 JavaScript 提交中击败了 77.20% 的用户

内存消耗 : 35.1 MB , 在所有 JavaScript 提交中击败了 81.36% 的用户
