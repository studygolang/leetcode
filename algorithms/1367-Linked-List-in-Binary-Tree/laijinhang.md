**代码**

```go
func isSubPath(head *ListNode, root *TreeNode) bool {
	if head == nil {
		return true
	}
	if root == nil {
		return false
	}
	return dfs(head, root) || isSubPath(head, root.Left) || isSubPath(head, root.Right)
}

func dfs(l *ListNode, root *TreeNode) bool {
	if l == nil {
		return true
	}
	if root == nil {
		return false
	}
	if root.Val != l.Val {
		return false
	}
	return dfs(l.Next, root.Left) || dfs(l.Next, root.Right)
}
```