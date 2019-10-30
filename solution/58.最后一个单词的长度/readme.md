# 58. 最后一个单词的长度

+ 题目地址：[leetcode](https://leetcode-cn.com/problems/length-of-last-word/)
+ 题目难度：easy

## 思路

唯一需要考虑的是去除前后空格后再取最后一个单词长度。

## 解答

```js
/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLastWord = function(s) {
    if (!s) {
        return 0;
    } else {
        let ns = s.trim().replace(/(.+)?\s/g, '');
        return ns.length;
    }
};
```

## 性能

执行用时 : 60 ms, 在所有 javascript 提交中击败了 92.80% 的用户

内存消耗 : 33.7 MB, 在所有 javascript 提交中击败了 42.46% 的用户
