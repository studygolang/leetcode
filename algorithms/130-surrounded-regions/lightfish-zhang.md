## 130.surrounded regions

## 解法

关键字：深度优先搜索、上色

- 分析题目，是要将没有连通边缘的 'O' 节点替换为 'X'
- 反过来，先搜索连通边缘的 'O' 节点，上色标记为 'Y'，最后遍历矩阵的所有节点，将 'O' 改为 'X'，将 'Y' 改回 'O'
- DFS 与 BFS 都可以，如果输入为大数，为避免堆栈溢出，DFS 要使用队列，BFS 要使用堆


```golang
func solve(board [][]byte) {
	h := len(board)
	if h == 0 {
		return
	}
	w := len(board[0])
	var dfs func(x, y int)
	dfs = func(x, y int) {
		if x < 0 ||
			x >= w ||
			y < 0 ||
			y >= h ||
			board[y][x] != 'O' {
			return
		}
		board[y][x] = 'Y'
		dfs(x+1, y)
		dfs(x-1, y)
		dfs(x, y+1)
		dfs(x, y-1)
	}

	for i := 0; i < w; i++ {
		dfs(i, 0)
		dfs(i, h-1)
	}
	for i := 1; i < h-1; i++ {
		dfs(0, i)
		dfs(w-1, i)
	}

	for i := 0; i < w; i++ {
		for j := 0; j < h; j++ {
			if board[j][i] == 'Y' {
				board[j][i] = 'O'
			} else if board[j][i] == 'O' {
				board[j][i] = 'X'
			}
		}
	}

}
```