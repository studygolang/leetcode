```golang
func integerBreak(n int) int {
    
    res := make([]int, n+1)
    res[0], res[1] = 0, 1
    for i := 2; i <= n; i++ {
        maxProduct := -1 << 31
        for j := 1; j <= i - 1; j++ {
            maxProduct = max(maxProduct, j*(i-j), j*res[i-j])
        }
        res[i] = maxProduct
    }
    
    return res[n]
}

func max(a, b, c int) int {
    var res int
    if a > b {
        res = a
    } else {
        res = b
    }
    
    if res < c {
       res = c 
    }
    
    return res
}
```
