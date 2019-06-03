# 7.整数反转

+ 题目地址：[leetcode](https://leetcode-cn.com/problems/reverse-integer/submissions/)
+ 题目难度：sasy

## 思路

反转并对负号做判断比较简单，再使用try catch 来防止溢出报错。

## 解答

```js
/**
 * @param {number} x
 * @return {number}
 */
var reverse = function(x) {
    let arr = String(x).split('');
    let first = '';
    let result = 0;
    // 判断首位是否负号
    if (arr[0] === '-') {
        first = arr[0];
        arr.shift();
    }
    // 反转并插入负号
    arr = arr.reverse();
    arr.unshift(first);
    
    // 使用try catch 防止溢出报错
    try {
        result = Number(arr.join(''));
        // 题目要求假设只能存储32位整数，溢出返回0
        if (result >= Math.pow(-2, 31) && result <= Math.pow(2, 31) - 1) {
            return result;
        } else {
            return 0;
        }
    } catch (err) {
        return result;
    }
};
```

## 性能

执行用时 : 96 ms, 在Reverse Integer的JavaScript提交中击败了98.36% 的用户

内存消耗 : 35.7 MB, 在Reverse Integer的JavaScript提交中击败了58.85% 的用户