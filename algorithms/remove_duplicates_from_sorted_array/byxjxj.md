```golang
func removeDuplicates(nums []int) int {
    
    if len(nums) == 0 {
        return 0
    }

    res := 1
    cur := nums[0]
    for _, v := range nums {
        if v != cur {
            nums[res] = v
            cur = v
            res++
        }
    }

    return res
}
```
