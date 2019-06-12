```golang
func getRow(rowIndex int) []int {
    
    res := make([]int, rowIndex+1)
    
    for i := 0; i <= rowIndex; i++ {
        for j := i; j >= 0; j-- {
            if j == 0 || j == i {
                res[j] = 1
            } else {
                res[j] = res[j-1] + res[j]
            }
        }
    }
    
    return res
}
```
