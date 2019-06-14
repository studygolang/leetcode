44ms，7.7Mb，破坏数组内数据了，应该有不破坏数据的解法
```
func removeDuplicates(nums []int) int {
    res, cur := 0, 0
    for ; cur < len(nums); cur++ {
        if nums[res] != nums[cur] {
            res++
            nums[res] = nums[cur]
        }
    }
    return res+1
}
```
