指针操作
```golang
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func swapPairs(head *ListNode) *ListNode {
	res := head
	first := true
	tmp := &ListNode{}
	for head != nil {
		if head.Next != nil {
			temp := head.Next
			head.Next = temp.Next
			temp.Next = head
			if first {
				res = temp
				first = false
			} else {
				tmp.Next = temp
			}
			tmp = head
		}
		head = head.Next
	}
	return res
}
```