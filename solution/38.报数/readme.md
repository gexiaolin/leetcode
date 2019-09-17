# 38.报数

+ 题目地址：[leetcode](https://leetcode-cn.com/problems/count-and-say/)
+ 题目难度：easy

## 思路

正则匹配，取到匹配数组后处理累加返回值。此题主要使用了[Array.prototype.reduce](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)方法。

## 解答

```js
/**
 * @param {number} n
 * @return {string}
 */
var countAndSay = function(n) {
    if (n < 1 || n > 30) return false;
    
    let result = '1';
    for (let i = 1; i < n; i++) {
        result = result.match(/1+|2+|3+/g).reduce((pre, cur) => {
            return pre += (cur.length + cur[0]);
        }, '');
    }
    return result;
};
```

## 性能

执行用时 : 68 ms , 在所有 JavaScript 提交中击败了 97.71% 的用户
内存消耗 : 35.5 MB , 在所有 JavaScript 提交中击败了 40.94% 的用户
