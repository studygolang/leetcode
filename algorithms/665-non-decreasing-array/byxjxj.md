```golang
func checkPossibility(nums []int) bool {
    
    count := 0
    
    for i := 1; i < len(nums); i++ {
        if nums[i-1] > nums[i] {
            count++
            if count > 1 {
                return false
            }
            
            if i - 2 < 0 || nums[i-2] <= nums[i] {
                nums[i-1] = nums[i]
            } else {
                nums[i] = nums[i-1]
            }
        }       
    }
    
    return true
}
```
