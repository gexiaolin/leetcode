# 6.Z字形变换

+ 题目地址：[leetcode](https://leetcode-cn.com/problems/plus-one/)
+ 题目难度：easy

## 思路

倒序便利，保存进位，如果进位为0即可break并返回结果。

## 解答

```js
/**
 * @param {number[]} digits
 * @return {number[]}
 */
var plusOne = function(digits) {
    let add = 0;
    let len = digits.length;
    
    for (let i = len - 1; i >= 0; i--) {
        let sum = add ? digits[i] + add : digits[i] + 1;
        if (sum >= 10) {
            digits[i] = sum % 10;
            i === 0 ? digits.unshift(1) : add = 1;
        } else {
            digits[i] = sum;
            break;
        } 
        
    }
    
    return digits;
};
```

## 性能

执行用时 : 68 ms , 在所有 JavaScript 提交中击败了 91.37% 的用户

内存消耗 : 33.6 MB , 在所有 JavaScript 提交中击败了 69.54% 的用户