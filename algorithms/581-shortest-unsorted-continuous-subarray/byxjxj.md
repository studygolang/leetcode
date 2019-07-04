```golang
func findUnsortedSubarray(nums []int) int {
    
    left, right := 0, -1
    max, min := nums[0], nums[len(nums)-1]
  
    for i := range nums {
        if max <= nums[i] {
            max = nums[i]
        } else {
            right = i
        }
        
        j := len(nums) - i - 1
        if min >= nums[j] {
            min = nums[j]
        } else {
            left = j
        }
    }
    
    return right - left + 1       
}
```
