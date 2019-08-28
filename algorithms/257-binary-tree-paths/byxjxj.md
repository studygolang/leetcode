```golang
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
func binaryTreePaths(root *TreeNode) []string {
    
    if root == nil {
        return []string{}
    }
    
    res := []string{}
    tmp := ""
    var dfs func(*TreeNode, string)
    dfs = func(root *TreeNode, tmp string) {
        if root == nil {
            return
        }
        if len(tmp) == 0 {
            tmp += strconv.Itoa(root.Val)
        } else {
            tmp += "->" + strconv.Itoa(root.Val)
        }
        if root.Left == nil && root.Right == nil {
            res = append(res, tmp)
        }
        dfs(root.Left, tmp)
        dfs(root.Right, tmp)
        
        tmp = ""
    }
    
    dfs(root, tmp)
    
    return res
}
```
