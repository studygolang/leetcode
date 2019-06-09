### 題目

[2. Add Two Numbers](https://leetcode.com/problems/add-two-numbers/)

### 解題思路

這題想通就不難了，遍歷兩個鏈表相加即可。
進位的部分要多練習。

### 代碼

```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func addTwoNumbers(l1 *ListNode, l2 *ListNode) *ListNode {
	dummy := ListNode{}
	head := &dummy
	carry := 0

	for l1 != nil || l2 != nil || carry != 0 {
		sum := 0

		if l1 != nil {
			sum += l1.Val
			l1 = l1.Next
		}
		if l2 != nil {
			sum += l2.Val
			l2 = l2.Next
		}

        sum += carry
        // 取出進位值
		carry = sum / 10

		head.Next = &ListNode{Val: sum % 10}
		head = head.Next
	}

	return dummy.Next
}
```
