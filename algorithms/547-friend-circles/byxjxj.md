```golang
func findCircleNum(M [][]int) int {
    
    if len(M) == 0 || len(M[0]) == 0 {
        return 0
    }
    
    set := Constructor(len(M))
    for i := range M {
        for j := range M[i] {
            if M[i][j] == 1 && set.Find(i) != set.Find(j) {
                set.Union(i, j)
            }
        }
    }
    
    res := 0
    for i, v := range set {
        if i == v {
            res++
        }
    }
    
    return res    
}

type disjoinSet []int

func Constructor(size int) disjoinSet {
    set := make(disjoinSet, size)
    for i := range set {
        set[i] = i
    }
    return set
}

func (d disjoinSet) Find(x int) int {
    if d[x] == x {
        return x
    } else {
        d[x] = d.Find(d[x])
        return d[x]
    }
}

func (d disjoinSet) Union(x, y int) {
    fx, fy := d.Find(x), d.Find(y)
    if fx != fy {
        d[fx] = fy
    }
}
```
