# 989.数组形式的整数加法

+ 题目地址：[leetcode](https://leetcode-cn.com/problems/add-to-array-form-of-integer/)
+ 题目难度：easy

## 思路

考虑边界情况，对K做位数递减操作。

## 解答

```js
/**
 * @param {number[]} A
 * @param {number} K
 * @return {number[]}
 */
var addToArrayForm = function(A, K) {
    let result = A;
    let i = A.length - 1;
    let borrow = 0;
    
    while (i >= 0 || K) {
        if (borrow === 0 && !K) break;
        
        let sum;
        sum = (A[i] || 0) + (K % 10 || 0) + borrow;
        borrow = sum >= 10 ? 1 : 0;

        if (i < 0) {
            result.unshift(sum % 10);
        } else {
            result[i] = sum % 10;
        }
        
        i--;
        K = parseInt(K / 10);
    }
    
    if (borrow === 1) result.unshift(1);
    
    return result;
};
```

## 性能

执行用时 : 128 ms  在所有 javascript 提交中击败了 98.50% 的用户

内存消耗 : 38.5 MB , 在所有 javascript 提交中击败了 85.18% 的用户
