```golang
func findMaxConsecutiveOnes(nums []int) int {
    
    tmp, max := 0, 0
    
    for _, v := range nums {
        if v == 1 {
            tmp++
        } else {
            tmp = 0
        }
        
        if max < tmp {
            max = tmp
        }
    }
    
    return max  
}
```
