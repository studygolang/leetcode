```golang
func climbStairs(n int) int {
    
    if n <= 2 {
        return n
    }
    
    pre, res := 1, 2
    for i := 3; i <= n; i++ {
        pre, res = res, pre + res
    }
    
    return res
}
```
