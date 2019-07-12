```golang
func findShortestSubArray(nums []int) int {
    
    size := len(nums)
    first := make(map[int]int, size)
    count := make(map[int]int, size)
    maxCount, minLen := 0, size
    
    for i, v:= range nums {
        count[v]++
        if count[v] == 1 {
            first[v] = i
        } 
        l := i - first[v] + 1
        
        if maxCount < count[v] || (maxCount == count[v] && l < minLen) {
            maxCount = count[v]
            minLen = l
        }
    }
    
    return minLen    
}
```
