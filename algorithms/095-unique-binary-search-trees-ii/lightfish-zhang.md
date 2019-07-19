#  95：不同的二叉搜索树 II

## 解法

遍历 1~n，当每一个i作为root节点时，求左右子树，这时，左右子树的求解是一个递归。这是一个动态规划的套路，只要求到最小解：空子树(nil)与叶子节点，动态规划的基石找到了。

加上缓存，执行效率还是很快的

```
✔ Accepted
  ✔ 9/9 cases passed (28 ms)
  ✔ Your runtime beats 94 % of golang submissions
  ✔ Your memory usage beats 100 % of golang submissions (8 MB)
```


```golang
type Pair struct {
	a, b interface{}
}

func generateTrees(n int) []*TreeNode {
	if n < 1 {
		return []*TreeNode{}
	}
	cache := make(map[Pair][]*TreeNode)
	return createTrees(1, n, cache)
}

func createTrees(start, end int, cache map[Pair][]*TreeNode) []*TreeNode {
	var ret []*TreeNode
	p := Pair{start, end}
	if ret, ok := cache[p]; ok {
		return ret
	}
	if start > end {
		ret = []*TreeNode{nil}
		cache[p] = ret
		return ret
	}
	if start == end {
		node := &TreeNode{
			Val:   start,
			Left:  nil,
			Right: nil,
		}
		ret = []*TreeNode{node}
		cache[p] = ret
		return ret
	}
	ret = make([]*TreeNode, 0)
	for i := start; i <= end; i++ {
		lefts := createTrees(start, i-1, cache)
		rights := createTrees(i+1, end, cache)
		for _, left := range lefts {
			for _, right := range rights {
				node := &TreeNode{
					Val:   i,
					Left:  left,
					Right: right,
				}
				ret = append(ret, node)
			}
		}
	}
	cache[p] = ret
	return ret
}
```