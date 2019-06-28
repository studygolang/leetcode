1、哈希表

Runtime: 12 ms, faster than 11.61% of Go online submissions for Linked List Cycle.

Memory Usage: 5.1 MB, less than 8.63% of Go online submissions for Linked List Cycle.
```
func hasCycle(head *ListNode) bool {
    if head == nil {
        return false
    }
    res := make(map[*ListNode]bool, 0)
    for head != nil {
        if _, ok := res[head]; ok {
            return true
        } else {
            res[head] = true
        }
        head = head.Next
    }
    return false
}
```

２、追赶

Runtime: 4 ms, faster than 99.48% of Go online submissions for Linked List Cycle.

Memory Usage: 3.8 MB, less than 100.00% of Go online submissions for Linked List Cycle.
```
func hasCycle(head *ListNode) bool {
    if head == nil || head.Next == nil {
        return false
    }
    slow, fast := head, head.Next
    for slow != fast {
        if fast == nil || fast.Next == nil {
            return false
        }
        slow = slow.Next
        fast = fast.Next.Next
    }
    return true
}
```
