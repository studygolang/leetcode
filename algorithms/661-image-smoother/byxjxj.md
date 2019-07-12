```golang
func imageSmoother(M [][]int) [][]int {
    
    res := make([][]int, len(M))
    for i := range res {
        res[i] = make([]int, len(M[i]))
    }
    
    x := [8]int{-1, 1, 0, 0, -1, -1, 1, 1}
    y := [8]int{0, 0, -1, 1, -1, 1, -1, 1}
    
    for i := range M {
        for j := range M[i] {
            sum, count := M[i][j], 1
            for k := 0; k < 8; k++ {
                if i+x[k] >= 0 && i+x[k] < len(M) && j+y[k] >= 0 && j+y[k] < len(M[i]) {
                    sum += M[i+x[k]][j+y[k]]
                    count++
                }
            }
            
            res[i][j] = sum / count
        }
    }
    
    return res
}
```
