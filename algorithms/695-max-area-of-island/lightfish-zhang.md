# 695 max area of island

## 解法

关键字：广度优先搜索、上色

1. 遍历矩阵上每一个坐标
2. 遇到 `0` 时忽略
3. 遇到 `1` 的坐标时累计面积且将该点修改为 `0`，从该坐标起进行广度优先搜索，重复步骤2

```golang

func maxAreaOfIsland(grid [][]int) int {
	h := len(grid)
	if h == 0 {
		return 0
	}
	w := len(grid[0])
	res := 0
	for i := 0; i < h; i++ {
		for j := 0; j < w; j++ {
			res = maxInt(res, area(grid, j, i, w, h))
		}
	}
	return res
}

func area(grid [][]int, x, y, w, h int) int {
	if x >= w || x < 0 || y >= h || y < 0 || grid[y][x] == 0 {
		return 0
	}
	grid[y][x] = 0
	return 1 + area(grid, x+1, y, w, h) + area(grid, x-1, y, w, h) + area(grid, x, y-1, w, h) + area(grid, x, y+1, w, h)
}

func maxInt(x, y int) int {
	if x > y {
		return x
	}
	return y
}
```