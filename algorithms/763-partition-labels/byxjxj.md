```golang
func partitionLabels(S string) []int {
    
    last := make(map[rune]int, 26)
    for i, c := range S {
        last[c] = i
    }
    
    firstC, lastC := 0, 0
    res := make([]int, 0)
    for i, c := range S {
        if last[c] > lastC {
            lastC = last[c]
        }
        if i == lastC {
            res = append(res, lastC-firstC+1)
            firstC = i + 1
        } 
    }
    
    return res
}
```
