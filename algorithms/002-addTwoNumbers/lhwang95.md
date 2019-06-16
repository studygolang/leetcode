```
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
