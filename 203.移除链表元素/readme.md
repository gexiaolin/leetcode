# 203.移除链表元素

+ 题目地址：[leetcode](https://leetcode-cn.com/problems/remove-linked-list-elements/submissions/)
+ 题目难度：easy
+ 数据结构：[链表](https://baike.baidu.com/item/%E9%93%BE%E8%A1%A8)

## 思路

遍历链表，把匹配到的指定元素的前一个元素的next指向匹配元素的next。


注意：该思路无法解决匹配到链表头元素的情况，所以需要先对链表头元素的匹配情况作处理。

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
 * @param {ListNode} head
 * @param {number} val
 * @return {ListNode}
 */
var removeElements = function(head, val) {
    while (head && head.val === val) {
        head = head.next;
    }
    let preNode = head;
    while (preNode && preNode.next) {
        if (preNode.next.val === val) {
            preNode.next = preNode.next.next;
        } else {
            preNode = preNode.next;
        }
    }
    return head;
};
```

## 性能

执行用时 : 116 ms, 在Remove Linked List Elements的JavaScript提交中击败了91.22% 的用户   
内存消耗 : 37.4 MB, 在Remove Linked List Elements的JavaScript提交中击败了26.50% 的用户