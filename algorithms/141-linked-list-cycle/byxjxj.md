```golang
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func hasCycle(head *ListNode) bool {
    
    if head != nil {
        fast, slow := head, head
    
        for fast.Next != nil && fast.Next.Next != nil {
            fast = fast.Next.Next
            slow = slow.Next
            if slow == fast {
                return true
            }
        } 
    }
    
    return false
}
```
