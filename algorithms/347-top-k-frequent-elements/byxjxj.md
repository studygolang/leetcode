```golang
func topKFrequent(nums []int, k int) []int {
    
    frequent := make(map[int]int, len(nums))    
    for _, v := range nums {
        frequent[v]++
    }
    
    count := make([]int, 0, len(frequent))
    for _, f := range frequent {
        count = append(count, f)
    }
    
    sort.Ints(count)
    
    min := count[len(count)-k]
    
    res := make([]int, 0, k)
    for k, v := range frequent {
        if v >= min {
            res = append(res, k)
        }
    }
    
    return res 
}
```
