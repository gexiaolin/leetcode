# 20.有效的括号

+ 题目地址：[leetcode](https://leetcode-cn.com/problems/valid-parentheses/)
+ 题目难度：easy

## 思路

引入栈的概念，遍历字符串，把当前字符压入栈。如果下一个字符和当前字符可以组成一对有效括号（'()'或'{}'或者'[]'），则把当前字符推出栈。如果最终栈为空，则为有效括号。

我们可以用数组模拟栈，也可以直接用字符串来模拟栈，实现后入先出。

## 解答

```js
/**
 * @param {string} s
 * @return {boolean}
 */
var isValid = function(s) {
    const sMap = {
        ')': '(',
        ']': '[',
        '}': '{'
    };
    let result = '';
    
    for (let i = 0; i < s.length; i++) {
        let len = result.length;
        let lastS = result[len - 1];
        let currentS = s[i];
        if (i === 0 || currentS === '(' || currentS === '[' || currentS === '{' || sMap[currentS] !== lastS) {
            result += currentS;
        } else {
            result = result.slice(0, len - 1);
        }
    }
    
    return result === '';
};
```

## 性能

Runtime: 52 ms, faster than 94.50% of JavaScript online submissions for Valid Parentheses.

Memory Usage: 37.1 MB, less than 5.01% of JavaScript online submissions for Valid Parentheses.