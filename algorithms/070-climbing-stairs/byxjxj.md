```golang
func climbStairs(n int) int {
    
    if n <= 1 {
        return n
    }
    
    tmp1, tmp2 := 1, 1
    res := 0
    for i := 2; i <= n; i++ {
        res = tmp1 + tmp2
        tmp1, tmp2 = tmp2, res
    }
    
    return res
}
```
