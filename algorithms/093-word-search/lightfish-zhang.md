# 79. word search

## 解法

- 一旦找到立马返回结果，使用深度优先搜索
- 注意的是，搜索路径上，不要走回头路

```golang
func exist(board [][]byte, word string) bool {
	// 判断地图的边界
	h := len(board)
	if h == 0 {
		return false
	}
	w := len(board[0])
	if w == 0 {
		return false
	}
	// 判断搜索路径长度的合法
	if len(word) == 0 || len(word) > h*w {
		return false
	}
	var search func(x, y, step int) bool
	search = func(x, y, step int) bool {
		if x < 0 || x >= w || y < 0 || y >= h || board[y][x] != word[step] {
			return false
		}
		next := step + 1
		if len(word) == next {
			return true
		}
		// 防止走回头路，掩盖来时的字母
		board[y][x] = ' '
		if search(x+1, y, next) ||
			search(x-1, y, next) ||
			search(x, y+1, next) ||
			search(x, y-1, next) {
			return true
		}
		// 修正字母，为下一次搜索铺路
		board[y][x] = word[step]
		return false
	}
	for i := 0; i < h; i++ {
		for j := 0; j < w; j++ {
			if search(j, i, 0) {
				return true
			}
		}
	}
	return false
}
```