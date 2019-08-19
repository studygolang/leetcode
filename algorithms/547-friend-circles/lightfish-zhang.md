# 547 friend circles

## 解法

深度优先搜索，对于每一个人，遍历他的好友，再遍历他的好友的好友，这样就遍历了一个朋友圈的人，同时标记已遍历过的好友，下次便不再遍历（这样可以跳过遍历过的朋友圈），每个朋友圈只遍历一次，这样就能统计朋友圈的数量了

```golang
func findCircleNum(M [][]int) int {
	n := len(M)
	if n == 0 {
		return 0
	}
	visted := make([]bool, n)
	res := 0
	var walk func(k int)
	walk = func(k int) {
		visted[k] = true
		for i := 0; i < n; i++ {
			if M[k][i] == 0 || visted[i] {
				continue
			}
			walk(i)
		}
	}
	for i := 0; i < n; i++ {
		if visted[i] {
			continue
		}
		walk(i)
		res++
	}
	return res
}
```