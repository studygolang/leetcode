### 題目

[141. Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/description/)

### 解題思路

利用快慢指針，快指針走兩步、慢指針走一步

### 代碼

```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func hasCycle(head *ListNode) bool {
	fast, slow := head, head

	for fast != nil {
		if fast.Next == nil {
			return false
		}
		fast = fast.Next.Next
		slow = slow.Next
		if fast == slow {
			return true
		}
	}
	return false
}
```
