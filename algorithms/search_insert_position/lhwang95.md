```
func searchInsert(nums []int, target int) int {
    res, length := 0, len(nums)
    if length == 0 || target < nums[0] {  // 
        return res
    } 
    for ; res < length; res++ {
        if nums[res] >= target {
            return res
        }
    }
    return res
}
```
