```golang
func arrayPairSum(nums []int) int {
    
    sort.Ints(nums)
    
    res := 0
    
    for i := 0; i < len(nums); i += 2 {
        res += nums[i]
    }
    
    return res
}
```
