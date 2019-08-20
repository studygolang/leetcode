# 417. pacific atlantic water flow

## 解法

从直觉来思考，从矩阵上的每个坐标开始深度优先搜索，路径的条件是节点权重递减，看它是否能走到左上/右下边缘，只不过搜索的目标点不再是一个单点，而是所有的边缘点。

换一个思路，从边缘点开始搜索


```golang
const (
	INT_MAX = int(^uint(0) >> 1)
	INT_MIN = ^INT_MAX
)

type pair struct {
	x, y int
}

func pacificAtlantic(matrix [][]int) [][]int {
	res := [][]int{}
	h := len(matrix)
	if h == 0 {
		return res
	}
	w := len(matrix[0])
	if w == 0 {
		return res
	}
	pacific := map[pair]bool{}
	alantic := map[pair]bool{}
	var dfs func(x, y int, pre int, visited map[pair]bool)
	dfs = func(x, y int, pre int, visited map[pair]bool) {
		if x < 0 || x >= w || y < 0 || y >= h || visited[pair{x, y}] {
			return
		}
		current := matrix[y][x]
		if current < pre {
			return
		}
		visited[pair{x, y}] = true
		dfs(x+1, y, current, visited)
		dfs(x-1, y, current, visited)
		dfs(x, y+1, current, visited)
		dfs(x, y-1, current, visited)
	}

	for i := 0; i < h; i++ {
		dfs(0, i, INT_MIN, pacific)
		dfs(w-1, i, INT_MIN, alantic)
	}
	for i := 0; i < w; i++ {
		dfs(i, 0, INT_MIN, pacific)
		dfs(i, h-1, INT_MIN, alantic)
	}
	for i := 0; i < h; i++ {
		for j := 0; j < w; j++ {
			if pacific[pair{j, i}] && alantic[pair{j, i}] {
				res = append(res, []int{i, j})
			}
		}
	}
	return res
}
```