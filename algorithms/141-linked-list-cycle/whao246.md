### 141. 环形链表

### 代码
```
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func hasCycle(head *ListNode) bool {
    if head==nil||head.Next==nil{
        return false
    }
    fast:=head.Next
    slow:=head
    for fast!=slow{
        if fast==nil||fast.Next==nil{
            return false
        }
        fast=fast.Next.Next
        slow=slow.Next
        
    }
    return true  
}
```