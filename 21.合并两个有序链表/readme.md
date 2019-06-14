# 21.合并两个有序链表

+ 题目地址：[leetcode](https://leetcode-cn.com/problems/merge-two-sorted-lists/)
+ 题目难度：easy
+ 数据结构：[链表](https://baike.baidu.com/item/%E9%93%BE%E8%A1%A8)

## 思路

通过迭代的思想，通过一个中间链表（l3）来记录合并l1和l2的记过，并通过每次的比较来定位next指针的指向。

时间复杂度O(n + m)。

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
var mergeTwoLists = function(l1, l2) {
    let curL1 = l1;
    let curL2 = l2;
    let l3 = new ListNode('head');
    let curL3 = l3;
    
    while (curL1 !== null || curL2 !== null) {
        if (curL1 === null) {
            curL3.next = curL2;
            break;
        }
        
        if (curL2 === null) {
            curL3.next = curL1;
            break;
        }
        if (curL1.val < curL2.val) {
            curL3.next = curL1;
            curL1 = curL1.next;
        } else {
            curL3.next = curL2;
            curL2 = curL2.next;
        }
        
        curL3 = curL3.next;
    }
    
    return l3.next;
};
```

## 性能

Runtime: 56 ms, faster than 97.34% of JavaScript online submissions for Merge Two Sorted Lists.

Memory Usage: 35.5 MB, less than 64.85% of JavaScript online submissions for Merge Two Sorted Lists.