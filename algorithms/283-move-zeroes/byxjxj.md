```golang
func moveZeroes(nums []int)  {
    
    j := 0
    for i, v := range nums {
        if v != 0 {
            nums[i], nums[j] = nums[j], nums[i]
            j++
        }
    }
}
```
