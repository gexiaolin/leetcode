# 9.回文数

+ 题目地址：[leetcode](https://leetcode-cn.com/problems/palindrome-number/)
+ 题目难度：easy

## 思路1

把Number转为String，遍历String的1/2长度，进行头尾比对。

## 解答1

```js
/**
 * @param {number} x
 * @return {boolean}
 */
var isPalindrome = function(x) {
    let str = String(x);
    let len = str.length;
    
    for (let i = 0; i < Math.floor(len / 2); i++) {
        if (str[i] !== str[len - 1 - i]) {
            return false;
        }
    }
    
    return true;
};
```

## 性能1

执行用时 : 272 ms, 在Palindrome Number的JavaScript提交中击败了99.38% 的用户

内存消耗 : 46.5 MB, 在Palindrome Number的JavaScript提交中击败了7.02% 的用户

## 思路2

题目有个进阶问题，不转String进行解答。我们可以考虑把Number的后半段反转，然后和前半段做比较，如果相同，即为回文数。

## 解答2

```js
/**
 * @param {number} x
 * @return {boolean}
 */
var isPalindrome = function(x) {
    if (x < 0 || (x % 10 === 0 && x !== 0)) {
        return false;
    }
    let n = 0;
    while (x > n) {
        n = n * 10 + x % 10;
        x = Math.floor(x / 10);
    }
    
    return x === n || x === Math.floor(n / 10);
};
```

## 性能2

执行用时 : 296 ms, 在Palindrome Number的JavaScript提交中击败了98.54% 的用户

内存消耗 : 45 MB, 在Palindrome Number的JavaScript提交中击败了89.10% 的用户
