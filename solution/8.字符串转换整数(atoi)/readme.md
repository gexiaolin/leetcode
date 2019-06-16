# 8.字符串转换整数(atoi)

+ 题目地址：[leetcode](https://leetcode-cn.com/problems/string-to-integer-atoi/)
+ 题目难度：medium

## 思路

正则匹配替换，并对边界做判断。

## 解答

```js
/**
 * @param {string} str
 * @return {number}
 */
var myAtoi = function(str) {
    var result;
    str = str.replace(/^\s+/, '');
    if (/^(\+|-)?\d+/.test(str)) {
        str.replace(/^(\+|-)?\d+/, val => {
            result = val;
            return 'A';
        });
        if (result < Math.pow(-2, 31)) {
            result = Math.pow(-2, 31)
        } else if (result > Math.pow(2, 31) - 1) {
            result = Math.pow(2, 31) - 1;
        }
        return result;
    } else {
        return 0;
    }
};
```

## 性能

执行用时 : 112 ms, 在String to Integer (atoi)的JavaScript提交中击败了91.15% 的用户

内存消耗 : 36 MB, 在String to Integer (atoi)的JavaScript提交中击败了40.08% 的用户