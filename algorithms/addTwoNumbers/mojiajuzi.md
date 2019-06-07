```golang
package main

import "fmt"

//ListNode 列表节点
type ListNode struct {
	Val  int
	Next *ListNode
}

func main() {
	l1 := &ListNode{}
	l1.node([]int{5})

	l2 := &ListNode{}
	l2.node([]int{5})

	p := addTwoNumbers(l1, l2)
	fmt.Println(p)

}

//计算相应位置的和
func addTwoNumbers(l1 *ListNode, l2 *ListNode) *ListNode {
	l := &ListNode{}
	recursive(l, l1, l2, 0)
	return l
}

//递归进行计算
func recursive(l, l1, l2 *ListNode, i int) *ListNode {
	if l1 == nil && l2 == nil {
		if i == 1 {
			l.Val = i
		}
	} else {
		l.Val = i
		i = 0
		if l1 != nil && l2 != nil {
			l.Val = l.Val + l1.Val + l2.Val
		} else {
			if l1 != nil {
				l.Val = l.Val + l1.Val
				l2 = &ListNode{}
			} else {
				l.Val = l.Val + l2.Val
				l1 = &ListNode{}
			}
		}
		if l.Val >= 10 {
			l.Val = l.Val - 10
			i = 1
		}
		if l1.Next != nil || l2.Next != nil {
			l.Next = &ListNode{}
			recursive(l.Next, l1.Next, l2.Next, i)
		} else {
			if i == 1 {
				l.Next = &ListNode{Val: i}
			}
		}
	}
	return l
}

//生成相应的数据节点
func (p *ListNode) node(s []int) {

	if len(s) == 1 {
		p.Val = s[0]
	} else {
		p.Val = s[0]
		p.Next = &ListNode{}
		(p.Next).node(s[1:])
	}
}

```