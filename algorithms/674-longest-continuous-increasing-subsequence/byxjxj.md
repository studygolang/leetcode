```golang
func findLengthOfLCIS(nums []int) int {
    
    if len(nums) <= 1 {
        return len(nums)
    }
    
    res, tmp := 1, 1
    
    for i := 1; i < len(nums); i++ {
        if nums[i] > nums[i-1] {
            tmp++
        } else {
            tmp = 1
        }
        
        if tmp > res {
            res = tmp
        }
    }
    
    return res
}
```
