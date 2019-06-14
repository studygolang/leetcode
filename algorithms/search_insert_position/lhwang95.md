4ms，3.1Mb
```
func searchInsert(nums []int, target int) int {
    res, length := 0, len(nums)
    if length == 0 || target < nums[0] {  // 如果切片为空或者所有元素都大于target，返回0
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
