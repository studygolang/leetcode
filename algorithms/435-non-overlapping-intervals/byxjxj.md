```golang
func eraseOverlapIntervals(intervals [][]int) int {
   
    sort.Sort(arr(intervals))
    res, j := 0, 0
    
    for i := 1; i < len(intervals); i++ {
        if intervals[i][0] < intervals[j][1] {
            if intervals[i][1] < intervals[j][1] {
                j = i
            }
            res++
        } else {
            j = i
        }
    } 
    
    return res
}

type arr [][]int

func (a arr) Len() int {
    return len(a) 
}

func (a arr) Less(i, j int) bool {
    return a[i][0] < a[j][0]
}

func (a arr) Swap(i, j int) {
    a[i], a[j] = a[j], a[i]
}
```
