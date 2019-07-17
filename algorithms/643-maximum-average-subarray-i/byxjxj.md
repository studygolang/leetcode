```golang
func findMaxAverage(nums []int, k int) float64 {
    
    tmp := 0
    
    for i := 0; i < k; i++ {
        tmp += nums[i]
    }
    
    max := tmp
    
    for i := 0; i < len(nums)-k; i++ {
        tmp = tmp - nums[i] + nums[i+k]
        if max < tmp {
            max = tmp
        }
    }
    
    return float64(max) / float64(k)  
}
```
