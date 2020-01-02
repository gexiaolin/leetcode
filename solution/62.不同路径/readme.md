# 62. 不同路径

+ 题目地址：[leetcode](https://leetcode-cn.com/problems/maximum-subarray/)
+ 题目难度：medium

## 思路

动态规划，拆解答案，坐标为 `m, n` 的格子路径数为 `m - 1, n` + `m, n - 1` 路径数的和。进行x轴和y轴的两层遍历，记录当前坐标的值。

时间复杂度O(m * n)。

## 解答

```js
/**
 * @param {number} m
 * @param {number} n
 * @return {number}
 */
var uniquePaths = function(m, n) {
    let map = {};

    for (let i = 0; i < m; i++) {
        map[i] = {};
        for (let j = 0; j < n; j++) {
            if (i === 0 || j === 0) {
                map[i][j] = 1;
            } else {
                map[i][j] = map[i - 1][j] + map[i][j - 1];
            }
        }
    }

    return map[m - 1][n - 1];
};
```

## 性能

执行用时 : 56 ms , 在所有 javascript 提交中击败了 95.30% 的用户

内存消耗 : 33.7 MB , 在所有 javascript 提交中击败了 71.51% 的用户
