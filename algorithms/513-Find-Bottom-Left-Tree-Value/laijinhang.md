**解题思路**

1. 用一个map去存储每层最左边值
2. 先遍历左子树，再遍历右子树

**代码**
```go
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
func findBottomLeftValue(root *TreeNode) int {
    m := make(map[int]int)  // 记录每层最左边
    traversal(root, m, 1)
    return m[len(m)]
}

func traversal(node *TreeNode, m map[int]int, h int) {
    if node == nil {
        return
    }
    if _, ok := m[h];!ok {
        m[h] = node.Val
    }
    traversal(node.Left, m, h+1)
    traversal(node.Right, m, h+1)
}
```