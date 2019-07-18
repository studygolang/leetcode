```golang
func findMinArrowShots(points [][]int) int {
    
    if len(points) <= 1  {
        return len(points)
    }
    
    sort.Slice(points, func (i, j int) bool {
        return points[i][1] < points[j][1]
    })
    res, i := 1, 0
    for j := 0; j < len(points); j++ {
        if points[i][1] < points[j][0] {
            res++
            i = j
        } 
    }
    
    return res   
}
```
