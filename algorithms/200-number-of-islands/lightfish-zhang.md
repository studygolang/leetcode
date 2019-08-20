# 200.number of is islands

## 解法

遍历矩阵，找到 '1'，岛屿数加一，然后深度优先搜索将相邻的 '1' 修改为 '0'，继续遍历

```golang
func numIslands(grid [][]byte) int {
	h := len(grid)
	if h == 0 {
		return 0
	}
	res := 0
	w := len(grid[0])
	for i := 0; i < h; i++ {
		for j := 0; j < w; j++ {
			if grid[i][j] == '1' {
				res++
				clear(grid, j, i, w, h)
			}
		}
	}
	return res
}

func clear(grid [][]byte, x, y, w, h int) {
	if x < 0 || x >= w || y < 0 || y >= h || grid[y][x] == '0' {
		return
	}
	grid[y][x] = '0'
	clear(grid, x+1, y, w, h)
	clear(grid, x-1, y, w, h)
	clear(grid, x, y+1, w, h)
	clear(grid, x, y-1, w, h)
}
```