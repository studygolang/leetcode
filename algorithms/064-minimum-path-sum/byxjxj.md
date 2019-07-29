```golang
func minPathSum(grid [][]int) int {
    
    if len(grid) == 0 || len(grid[0]) == 0 {
        return 0
    }
    
    maxInt := 1 << 63 - 1
    minSum := make([][]int, len(grid)+1)
    for i := range minSum {
        minSum[i] = make([]int, len(grid[0])+1)
        if i == 0 {
            for j := range minSum[i] {
                minSum[i][j] = maxInt
            }
        }
        minSum[i][0] = maxInt
    }
    minSum[0][1] = 0
    
    for i := range grid {
        for j := range grid[i] {
            minSum[i+1][j+1] = min(minSum[i+1][j], minSum[i][j+1]) + grid[i][j]
        }
    }
    
    return minSum[len(grid)][len(grid[0])]
}

func min(a, b int) int {
    if a > b {
        return b
    }
    
    return a
}
```
