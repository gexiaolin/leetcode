# 2.两数相加

+ 题目地址：[leetcode](https://leetcode-cn.com/problems/add-two-numbers/)
+ 题目难度：medium
+ 数据结构：[链表](https://baike.baidu.com/item/%E9%93%BE%E8%A1%A8)

## 思路

根据两个相加链表的当前位置，计算是否有升位，赋值给新链表的当前位。

## 解答

```js
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */
var addTwoNumbers = function(l1, l2) {
    let cur1 = l1,
        cur2 = l2,
        carry = 0,
        l3,
        cur3;
    while (cur1 || cur2 || carry) {
        let num1 = 0, num2 = 0;
        if (cur1) {
            num1 = cur1.val;
            cur1 = cur1.next;
        }
        if (cur2) {
            num2 = cur2.val;
            cur2 = cur2.next;
        }
        let sum = (num1 + num2 + carry) % 10;
        carry = parseInt((num1 + num2 + carry) / 10);
        if (!l3) {
            l3 = new ListNode(sum);
            cur3 = l3;
        } else {
            cur3.next = new ListNode(sum);
            cur3 = cur3.next;
        }
    }
    
    return l3;
};
```

## 性能

执行用时 : 168 ms, 在Add Two Numbers的JavaScript提交中击败了96.86% 的用户   
内存消耗 : 38.8 MB, 在Add Two Numbers的JavaScript提交中击败了29.09% 的用户
