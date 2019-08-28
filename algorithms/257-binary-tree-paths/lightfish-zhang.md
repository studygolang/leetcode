# 257. binary tree paths

## 解法

递归的深度优先搜索，遍历到叶子节点，再以叶子节点为起点，把搜索路径在函数堆栈上传递回来，这个方法有个弊端，树特别大时会造成堆栈溢出


```golang
import (
	"strconv"
	"strings"
)

func binaryTreePaths(root *TreeNode) []string {
	if root == nil {
		return []string{}
	}
	ret := []string{}
	path := search(root)
	for _, p := range path {
		var b strings.Builder
		for i := len(p) - 1; i > 0; i-- {
			b.WriteString(strconv.Itoa(p[i]))
			b.WriteString("->")
		}
		b.WriteString(strconv.Itoa(p[0]))
		ret = append(ret, b.String())
	}
	return ret
}

func search(root *TreeNode) [][]int {
	if root == nil {
		return [][]int{}
	}
	ret := [][]int{}

	if root.Left != nil {
		ret1 := search(root.Left)
		for i, _ := range ret1 {
			ret1[i] = append(ret1[i], root.Val)
		}
		ret = append(ret, ret1...)
	}
	if root.Right != nil {
		ret2 := search(root.Right)
		for i, _ := range ret2 {
			ret2[i] = append(ret2[i], root.Val)
		}
		ret = append(ret, ret2...)
	}
	if len(ret) == 0 {
		ret = [][]int{{root.Val}}
	}
	return ret
}
```