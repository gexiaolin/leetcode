# 120. 三角形最小路径和

+ 题目地址：[leetcode](https://leetcode-cn.com/problems/triangle/)
+ 题目难度：medium

## 思路

动态规划。自上而下记录对应位置的最优解，状态转移方程：f(n) = f(n) + f(n - 1)

时间复杂度O(n)，一次遍历

空间复杂度O(1)，在当前数组操作，不申请额外数组内存

## 解答

```js
/**
 * @param {number[][]} triangle
 * @return {number}
 */
var minimumTotal = function(triangle) {
    // 边界判断
    if (!triangle.length) return 0;
    if (triangle.length === 1) return triangle[0][0];

    let result;
    for (let i = 1; i < triangle.length; i++) {
        let current = triangle[i];
        let prev = triangle[i - 1];

        for (let j = 0; j < current.length; j++) {
            // 记录 `i, j` 坐标的最优解
            if (j === 0) {
                current[j] += prev[j];
            } else if (j === current.length - 1) {
                current[j] += prev[current.length - 2];
            } else {
                current[j] = Math.min(current[j] + prev[j], current[j] + prev[j - 1]);
            }

            // 最后一组数据，开始比较最终解
            if (i === triangle.length - 1) {
                if (j === 0) {
                    result = triangle[i][j];
                } else {
                    result = Math.min(result, current[j]);
                }
            }
        }
    }

    return result;
};
```

## 性能

执行用时 : 64 ms , 在所有 JavaScript 提交中击败了 83.41% 的用户

内存消耗 : 34.6 MB , 在所有 JavaScript 提交中击败了 85.19% 的用户
