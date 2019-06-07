## 题目

You are given two non-empty linked lists representing two non-negative integers. 

The digits are stored in reverse order and each of their nodes contain a single digit. 

Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.


```
Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
Explanation: 342 + 465 = 807.
```

[原题地址](https://leetcode.com/problems/add-two-numbers/)

```
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */

// 12ms, 5.1MB
func addTwoNumbers(l1 *ListNode, l2 *ListNode) *ListNode {
    var (
        cin int = 0 // 进位标志
        rootNode bool = true // 根节点标志
        head **ListNode = nil
        pre *ListNode = nil
    )
    for (l1 != nil) || (l2 != nil) {
        curNode := new(ListNode)
        if rootNode { // 定位根节
            head = &curNode
            rootNode = false
        } else {
            pre.Next = curNode
        }
        if (l1 != nil) && (l2 != nil) {
            curNode.Val = l1.Val + l2.Val + cin
            l1 = l1.Next
            l2 = l2.Next
        } else if (l1 == nil) && (l2 != nil) {
            curNode.Val = l2.Val + cin
            l2 = l2.Next
        } else if (l1 != nil) && (l2 == nil) {
            curNode.Val = l1.Val + cin
            l1 = l1.Next
        }
        if curNode.Val >= 10 {
            cin = 1
            curNode.Val -= 10
        } else {
            cin = 0
        }
        pre = curNode
    }
    if cin == 1 {
        pre.Next = &ListNode{
            Val : 1,
            Next : nil,
        }
        
    } else {
        pre.Next = nil
    }
    return *head
}
```
