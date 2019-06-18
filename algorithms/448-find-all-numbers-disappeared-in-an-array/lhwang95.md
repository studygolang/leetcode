标记法
Runtime: 368 ms, faster than 95.10% of Go online submissions for Find All Numbers Disappeared in an Array.

Memory Usage: 8.5 MB, less than 24.67% of Go online submissions for Find All Numbers Disappeared in an Array.
```
func findDisappearedNumbers(nums []int) []int {
    for i:=0; i<len(nums); i++ {
        temp := int(math.Abs(float64(nums[i])))-1
        if nums[temp] > 0 {
            nums[temp] = -nums[temp]
        }
    }
    res := make([]int, 0)
    for i, v := range nums {
        if v > 0 {
            res = append(res, i+1)
        }
    }
    return res
}
```

2、
