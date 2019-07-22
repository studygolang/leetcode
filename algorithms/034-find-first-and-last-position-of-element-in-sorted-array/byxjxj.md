```golang
func searchRange(nums []int, target int) []int {
        
    left, right := 0, len(nums) - 1
    first, last := -1, -1
    for left < right {
        mid := left + (right - left) >> 1
        if nums[mid] < target {
            left = mid + 1
        } else {
            right = mid
        }
    }
    if left >= 0 && left <= len(nums) - 1 && nums[left] == target {
       first = left
    } else {
        return []int{first, last}
    }
    
    right = len(nums) - 1
    for left >= 0 && left < right {
        mid := right - (right - left) >> 1 
        if nums[mid] > target {
            right = mid - 1
        } else {
            left = mid
        }
    }
    if nums[left] == target {
        last = left
    }
    
    return []int{first, last}
}
```
