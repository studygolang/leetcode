```golang
func containsNearbyDuplicate(nums []int, k int) bool {
    
    if k < 0 {
        return false
    }
    
    
    index := make(map[int]int, len(nums))
    
    for i, v := range nums {
        if j, ok := index[v]; ok && i - j <= k {
            return true
        }
        
        index[v] = i
    }
    
    return false
}
```
