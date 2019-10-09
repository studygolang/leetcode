
```golang
func mergeKLists(lists []*ListNode) *ListNode {
	lenList := len(lists)
	if lenList == 0 {
		return nil
	}
	res := lists[0]
	if lenList == 1 {
		return res
	}
	for i := 1; i < lenList; i++ {
		res = mergeTwoLists(res, lists[i])
	}
	return res
}
func mergeTwoLists(l1 *ListNode, l2 *ListNode) *ListNode {
	if l1 == nil {
		return l2
	}
	if l2 == nil {
		return l1
	}
	res := &ListNode{}
	if l1.Val < l2.Val {
		res.Val = l1.Val
		l1 = l1.Next
	} else {
		res.Val = l2.Val
		l2 = l2.Next
	}
	temp := res
	for l1 != nil || l2 != nil {
		if l1 == nil {
			temp.Next = l2
			return res
		}
		if l2 == nil {
			temp.Next = l1
			return res
		}
		if l1.Val < l2.Val {
			temp.Next = l1
			l1 = l1.Next
			temp = temp.Next
		} else {
			temp.Next = l2
			l2 = l2.Next
			temp = temp.Next
		}
	}
	return res
}
```