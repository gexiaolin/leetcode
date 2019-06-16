# 22.括号生成

## 思路

首先考虑起始和闭合括号的插入规则。在一个符合规则的插入过程中，当前指针位置及之前所有的的起始括号数量一定是要大于等于闭合括号，否则该字串不符合有效括号的规则。

根据上述规则，通过回溯法进行规则生成。

## 解答

```js
/**
 * @param {number} n
 * @return {string[]}
 */
var generateParenthesis = function(n) {
    let result = [];
    getStr('', 0, 0);
    
    function getStr (str, l, r) {
        if (r === n) {
            result.push(str);
            return false;
        }
        
        if (l < n) {
            getStr(str + '(', l + 1, r);
        }
        
        if (r < l) {
            getStr(str + ')', l, r + 1);
        }
    }
    
    return result;
};
```

## 性能

Runtime: 48 ms, faster than 98.54% of JavaScript online submissions for Generate Parentheses.

Memory Usage: 34.9 MB, less than 79.77% of JavaScript online submissions for Generate Parentheses.