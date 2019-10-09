时间复杂度：O(n)
```golang
func removeNthFromEnd(head *ListNode, n int) *ListNode {
	var temp, delNodeParent *ListNode
	temp = head
	delNodeParent = head //需要删除节点的父节点
	for i := 0; i < n; i++ {
		temp = temp.Next
	}
	if temp == nil { //判断是否删除头节点
		head = head.Next
		return head
	}
	for temp.Next != nil {
		temp = temp.Next
		delNodeParent = delNodeParent.Next
	}
	delNodeParent.Next = delNodeParent.Next.Next
	return head
}
```