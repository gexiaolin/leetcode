# 11.盛最多水的容器

+ 题目地址：[leetcode](https://leetcode-cn.com/problems/container-with-most-water/)
+ 题目难度：medium

## 思路

双指针查找。从宽度最大值开始计算面积，比较双指针的较小值移动一位，存储移动过程中的最大值。

一次扫描即可得到结果，时间复杂度O(n)。

## 解答

```js
/**
 * @param {number[]} height
 * @return {number}
 */
var maxArea = function(height) {
    let l = 0;
    let r = height.length - 1;
    let result = 0;
    
    while (l < r) {
        let h = Math.min(height[l], height[r]);
        result = Math.max(result, h * (r - l));
        
        height[l] < height[r] ? l += 1 : r -= 1;
    }
    
    return result;
};
```

## 性能

执行用时 : 80 ms, 在Container With Most Water的JavaScript提交中击败了98.36% 的用户

内存消耗 : 35.7 MB, 在Container With Most Water的JavaScript提交中击败了24.68% 的用户