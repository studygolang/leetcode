```golang
func lengthOfLIS(nums []int) int {
    
    if len(nums) == 0 {
        return 0
    }
    
    res := make([]int, 0, len(nums))
    for i := range nums {
        if i == 0 || nums[i] > res[len(res)-1] {
            res = append(res, nums[i])
        } else {
            l, r := 0, len(res)-1
            for l < r {
                mid := l + (r-l) >> 1
                if nums[i] > res[mid] {
                    l = mid + 1
                } else {
                    r = mid
                }
            }
            res[r] = nums[i]
        }
    }
    
    return len(res)
}
```
