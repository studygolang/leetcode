花里胡哨地用Go协程完成，为练习Go协程，对本题无特别意义
```golang
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */

func addTwoNumbers(l1 *ListNode, l2 *ListNode) *ListNode {
	l1Chan := make(chan int)
	l2Chan := make(chan int)
	//finishedChan := make(chan bool)
	var res = &ListNode{}
	cur := res
	count := 0
	tmp := 0
	go func() {
		for l1 != nil {
			l1Chan <- l1.Val
			l1 = l1.Next
		}
		close(l1Chan)
	}()
	go func() {
		for l2 != nil {
			l2Chan <- l2.Val
			l2 = l2.Next
		}
		close(l2Chan)
	}()

	bFirst := true
	for {
		tmp = 0
		l1Val, ok1 := <-l1Chan
		if ok1 {
			tmp = l1Val
		}
		l2Val, ok2 := <-l2Chan
		if ok2 {
			tmp += l2Val
		}
		if !ok1 && !ok2 {
			if count == 1 {
				cur.Next = &ListNode{Val: 1}
			}
			return res
		} else {
			if !bFirst {
				cur.Next = &ListNode{}
				cur = cur.Next
			}
		}
		cur.Val = tmp + count
		if cur.Val >= 10 {
			cur.Val = cur.Val % 10
			count = 1
		} else {
			count = 0
		}
		bFirst = false
	}
}
```