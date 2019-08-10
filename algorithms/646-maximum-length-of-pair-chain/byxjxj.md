```golang
func findLongestChain(pairs [][]int) int {
    
    if len(pairs) == 0 || len(pairs[0]) == 0 {
        return 0
    }
    
    sort.Slice(pairs, func(i, j int) bool {
        return pairs[i][1] < pairs[j][1]
    })
    
    res, end := 1, pairs[0][1]
    for _, pair := range pairs {
        if pair[0] > end {
            end = pair[1]
            res++
        }
    }
    
    return res
}
```
