同步遍历两个链表，对位相加并记录进位，当下一结点都为nil且无进位时，返回结果，耗时12ms。
```golang
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *      Val int
 *      Next *ListNode
 * }
 */

 func addTwoNumbers(l1 *ListNode, l2 *ListNode) *ListNode {
    
    res := &ListNode{}
    cur := res
    c := 0

    for l1 != nil || l2 != nil || c != 0 {
        
        if l1 != nil {
            cur.Val += l1.Val
            l1 = l1.Next
        }
        if l2 != nil {
            cur.Val += l2.Val
            l2 = l2.Next
        }

        cur.Val += c
        c = cur.Val / 10
        cur.Val %= 10
        
        if l1 == nil && l2 == nil && c == 0 {
            return res
        }

        cur.Next = &ListNode{}
        cur = cur.Next
    }

    return nil
 }
```
