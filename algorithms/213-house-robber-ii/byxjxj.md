```golang
func rob(nums []int) int {
    
    switch len(nums) {
        case 0:
        return 0
        case 1:
        return nums[0]
    }
    
    pre1, res1 := 0, 0 
    pre2, res2 := 0, 0
    for i := 0; i < len(nums) - 1; i++ {
        pre1, res1 = res1, max(res1, pre1+nums[i])
        pre2, res2 = res2, max(res2, pre2+nums[i+1])
    }
    
    return max(res1, res2)
}

func max(a, b int) int {
    if a > b {
        return a
    }
    
    return b
}
```
