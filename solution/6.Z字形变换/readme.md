# 6.Z字形变换

+ 题目地址：[leetcode](https://leetcode-cn.com/problems/zigzag-conversion/)
+ 题目难度：medium

## 思路

我们可以根据行数n来存储n个字符串，通过一次遍历依次把当前字符拼接到已存储的对应字符串上，最后把n个字符串再做一次拼接，就可以拿到最终需要的结果。

一次遍历，时间复杂度O(n)。

## 解答

```js
/**
 * @param {string} s
 * @param {number} numRows
 * @return {string}
 */
var convert = function(s, numRows) {
    // 通过一个数组来存储numRows个字符串
    let arr = [];
    // 记录当前下标
    let count = 0;
    // 当前应该是下标递增或是递减
    let add = true;
    // 如果numRows为1，直接返回字符串s
    if (numRows === 1) {
        return s;
    }
    // 遍历给定字符串
    for (let i = 0; i < s.length; i++) {
        // 需要判断arr[count]是否存在，防止出现undefined + 'a'这类情况
        arr[count] = arr[count] ? arr[count] + s[i] : s[i];
        // 当count计数到0时，接下来需要递增
        // 当count计数到numRows - 1时，接下来需要递减
        if (count === 0) {
            add = true;
        } else if (count === numRows - 1) {
            add = false;
        }
        // 根据递增递减情况，对下标count进行对应操作
        count = add ? count + 1 : count - 1;
    }
    
    // 拼接多个元素并返回结果
    return arr.join('');
};
```

## 性能

执行用时 : 120 ms, 在ZigZag Conversion的JavaScript提交中击败了97.80% 的用户

内存消耗 : 39.1 MB, 在ZigZag Conversion的JavaScript提交中击败了46.97% 的用户