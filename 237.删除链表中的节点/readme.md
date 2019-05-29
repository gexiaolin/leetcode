# 237.删除链表中的节点

+ 题目地址：[leetcode](https://leetcode-cn.com/problems/delete-node-in-a-linked-list/)
+ 题目难度：easy
+ 数据结构：[链表](https://baike.baidu.com/item/%E9%93%BE%E8%A1%A8)

## 思路

删除链表的节点，其实就是将指定删除节点的前一个节点的next指向指定删除节点的next属性。

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
 * @param {ListNode} node
 * @return {void} Do not return anything, modify node in-place instead.
 */
var deleteNode = function(node) {
    node.val = node.next.val;
    node.next = node.next.next;
};
```

## 性能

执行用时 : 92 ms, 在Delete Node in a Linked List的JavaScript提交中击败了98.33% 的用户   
内存消耗 : 35.3 MB, 在Delete Node in a Linked List的JavaScript提交中击败了94.88% 的用户
