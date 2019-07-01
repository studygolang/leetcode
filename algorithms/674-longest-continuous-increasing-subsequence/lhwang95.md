Runtime: 8 ms, faster than 95.69% of Go online submissions for Longest Continuous Increasing Subsequence.

Memory Usage: 4.5 MB, less than 27.45% of Go online submissions for Longest Continuous Increasing Subsequence.
```
func findLengthOfLCIS(nums []int) int {
    if len(nums) == 0 {
        return 0
    }
    res, max := 1, -1
    for i:=0; i<len(nums)-1; i++ {
        if nums[i] < nums[i+1] {
            res++
        } else {
            if max < res {
                max = res
            }
            res = 1
        }
    }
    if max < res {
        max = res
    }
    return max
}
```
