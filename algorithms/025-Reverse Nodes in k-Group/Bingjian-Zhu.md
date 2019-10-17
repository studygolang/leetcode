思路：找到前k个节点，然后反转链表，并记录末尾节点，然后把后续的反转的链表拼起来
```golang
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func reverseKGroup(head *ListNode, k int) *ListNode {
	if k == 1 || head == nil {
		return head
	}
	res := &ListNode{}
	temp := head
	times := 0
	end := &ListNode{}
	first := true
	for head != nil {
		times++
		if times == k {
			next := head.Next
			head.Next = nil
			reve := reverse(temp)
			start := reve
			for start.Next != nil {
				start = start.Next
			}
			if first {
				res = reve
				first = false
			} else {
				end.Next = reve
			}
			end = start
			times = 1
			head = next
			temp = next
		}
		if head != nil {
			head = head.Next
		}
	}
	if first {
		res = temp
	}
	if temp != nil {
		end.Next = temp
	}
	return res
}

//链表反转
func reverse(head *ListNode) *ListNode {
	res := head
	for head != nil {
		if head.Next != nil {
			temp := head.Next
			head.Next = temp.Next
			temp.Next = res
			res = temp
		} else {
			head = head.Next
		}
	}
	return res
}
```