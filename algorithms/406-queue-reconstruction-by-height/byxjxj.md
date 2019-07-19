```golang
func reconstructQueue(people [][]int) [][]int {
    
    sort.Sort(arr(people)) 
    
    count := 0
    res := make([][]int, len(people))
    
    for i, p := range people {
        res[i] = make([]int, 2)
        for j := count; j >= p[1] + 1; j-- {
            res[j] = res[j-1]
        } 
        res[p[1]] = p
        
        count++
    }
    
    return res
}

type arr [][]int

func (a arr) Len() int {
    return len(a)
}

func (a arr) Less(i, j int) bool {
    if a[i][0] != a[j][0] {
        return a[i][0] > a[j][0]
    }
    return a[i][1] < a[j][1]
}

func (a arr) Swap(i, j int) {
    a[i], a[j] = a[j], a[i]
}
```
