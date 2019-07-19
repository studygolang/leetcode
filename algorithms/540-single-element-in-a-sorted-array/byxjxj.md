```golang
func singleNonDuplicate(nums []int) int {
    
    if len(nums) == 1 {
        return nums[0]
    }
            
    left, right := 0, len(nums) - 1
    
    for left < right {
        mid := left + (right - left) >> 1
        tmp := mid ^ 1
        if nums[mid] == nums[tmp] {
            left = mid + 1
        } else {
            right = mid
        }
    }
    
    return nums[left]
}
```
