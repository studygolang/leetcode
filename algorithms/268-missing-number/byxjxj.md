```golang
func missingNumber(nums []int) int {
    
    res := 0
    
    for i, v := range nums {
        res ^= i ^ v
    }
    
    return res^len(nums)
    
}
```
