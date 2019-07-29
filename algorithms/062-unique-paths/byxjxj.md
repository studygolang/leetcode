```golang
func uniquePaths(m int, n int) int {
    
    if m <= 0 || n <= 0 {
        return 0
    }
    
    res := make([][]int, m+1)
    for i := range res {
        res[i] = make([]int, n+1)
    }
    res[0][1] = 1
    for i := 1; i < m+1; i++ {
        for j := 1; j < n+1; j++ {
            res[i][j] = res[i-1][j] + res[i][j-1]
        }
    }
    
    return res[m][n]
}
```
