# 28.实现strStr()

+ 题目地址：[leetcode](https://leetcode-cn.com/problems/implement-strstr/)
+ 题目难度：easy

## 思路

使用split对字符串进行切割，根据切割后的元素数返回结果。（对不起我偷懒了。。）

## 解答

```js
/**
 * @param {string} haystack
 * @param {string} needle
 * @return {number}
 */
var strStr = function(haystack, needle) {
    if (needle === '') return 0;
    
    let res = haystack.split(needle);

    if (res.length === 1) {
        return -1;
    } else {
        return res[0].length;
    }
};
```

## 性能

Runtime: 52 ms, faster than 91.56% of JavaScript online submissions for Implement strStr().

Memory Usage: 34 MB, less than 65.78% of JavaScript online submissions for Implement strStr().
