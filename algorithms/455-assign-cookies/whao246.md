### 455. 分发饼干

### 代码
```
func findContentChildren(g []int, s []int) int {
    j:=0
    sort.Ints(g)
    sort.Ints(s)
    for i:=0;i<len(s)&&j<len(g);i++{
        if s[i]>=g[j]{
            j++
        }
    }
    return j
}
```