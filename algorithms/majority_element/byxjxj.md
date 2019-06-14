```golang
func majorityElement(nums []int) int {
    
    count := make(map[int]int)
    res := 0
    
    for _, v := range nums {
        count[v]++
        if count[v] >= len(nums)/2+1 {
            res = v
            break
        }
    }
    
    return res
}
```
