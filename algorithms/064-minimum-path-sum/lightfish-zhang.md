# 最小路径和

## 解法

注意题目的要点，路径只有两个方向，往下与往右

动态规划的思路:

- 找到状态转移方程，`dp[m][n] = grid[m][n] + min(dp[m-1][n], dp[m][n])`
- 空间复杂度上，需要申请一块 与输入 grid 同等大小的`n*m`空间，记录到达每一个坐标的路径和
- 需要初始化的值有 `dp[0][0] ... dp[0][n]` 与 `dp[0][0] ... dp[m][0]`


```golang
func minPathSum(grid [][]int) int {
	yl := len(grid)
	if yl == 0 {
		return 0
	}
	xl := len(grid[0])
	if xl == 0 {
		return 0
	}
	// malloc
	dp := make([][]int, yl)
	for i, _ := range dp {
		dp[i] = make([]int, xl)
	}
	dp[0][0] = grid[0][0]
	for i := 1; i < yl; i++ {
		dp[i][0] = grid[i][0] + dp[i-1][0]
	}
	for j := 1; j < xl; j++ {
		dp[0][j] = grid[0][j] + dp[0][j-1]
	}
	for i := 1; i < yl; i++ {
		for j := 1; j < xl; j++ {
			dp[i][j] = grid[i][j] + minInt(dp[i-1][j], dp[i][j-1])
		}
	}
	return dp[yl-1][xl-1]
}

func minInt(x, y int) int {
	if x < y {
		return x
	}
	return y
} 
```


基于以上，可以优化的地方还有：

- 空间复杂度降低为 `n*1` 的空间，不好理解，不写了