```golang
func findKthLargest(nums []int, k int) int {
    
    size := len(nums)
    targetPos := size - k
    l, r := 0, size - 1
    
    for {
        pivotIndex := partition(nums, l, r)
        if pivotIndex == targetPos {
            return nums[pivotIndex]
        } else if pivotIndex < targetPos {
            l = pivotIndex + 1
        } else {
            r = pivotIndex - 1
        }
    }
    
}

func partition(nums []int, l, r int) int {
    pivot := nums[l]
    i, j := l, r
    
    for i < j {
        for i < j && nums[j] > pivot {
            j--
        }
        for i < j && nums[i] <= pivot {
            i++
        }
        
        if i < j {
            nums[i], nums[j] = nums[j], nums[i]
        }
    }
    nums[i], nums[l] = nums[l], nums[i]
    
    return i
}
```
