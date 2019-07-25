```golang
func rob(nums []int) int {
    
    if len(nums) == 0 {
        return 0
    }
    
    pre, res := 0, 0
    for i := 0; i < len(nums); i++ {
        pre, res = res, max(res, pre+nums[i])
    }
    
    return res
}

func max(a, b int) int {
    if a > b {
        return a
    }
    
    return b
}
```
