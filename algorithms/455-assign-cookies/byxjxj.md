```golang
func findContentChildren(g []int, s []int) int {
    
    sort.Ints(g)
    sort.Ints(s)
    res, i, j := 0, 0, 0

    for i < len(g) && j < len(s) {
        if g[i] <= s[j] {
            i++
            res++
        }
        j++
    }
    
    return res
}
```
