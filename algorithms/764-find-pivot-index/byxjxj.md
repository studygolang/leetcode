```golang
func pivotIndex(nums []int) int {
    
    lSum, rSum := 0, 0
    for _, v := range nums {
        rSum += v
    }
    
    for i, v := range nums {
        rSum -= v
        if lSum == rSum {
            return i
        }
        lSum += v
    }
    
    return -1
}
```
