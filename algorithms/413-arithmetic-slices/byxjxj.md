```golang
func numberOfArithmeticSlices(A []int) int {
    
    if len(A) < 3 {
        return 0
    }
    
    count, res := 0, 0
    for i := 2; i < len(A); i++ {
        if A[i] - A[i-1] == A[i-1] - A[i-2] {
            count++
            res += count
        } else {
            count = 0
        }
    }
    
    return res
}
```
