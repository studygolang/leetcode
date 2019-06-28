Runtime: 20 ms, faster than 93.03% of Go online submissions for Find Pivot Index.

Memory Usage: 5.9 MB, less than 70.13% of Go online submissions for Find Pivot Index.
```
func pivotIndex(nums []int) int {
    length := len(nums)
    if length == 0 {
        return -1
    } else if length == 1 {
        return 0
    }
    left, right, curIndex := 0, 0, 0
    for i:=1; i<length; i++ {
        right += nums[i]
    }
    for left != right && curIndex<len(nums)-1 {
        left += nums[curIndex]
        right -= nums[curIndex+1]
        curIndex++
    }
    if curIndex == len(nums)-1 && left != right {
        return -1
    }
    return curIndex
}
```
