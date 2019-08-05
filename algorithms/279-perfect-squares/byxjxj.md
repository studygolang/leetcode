```golang
func numSquares(n int) int {
    
    dp := make([]int, n+1)
    
    for i := 0; i <= n; i++ {
        dp[i] = i
        for j := 1; i-j*j >= 0; j++ {
            dp[i] = min(dp[i], dp[i-j*j]+1)
        }
    }
    
    return dp[n]
}

func min(a, b int) int {
    if a > b {
        return b
    }
    
    return a
}
```
