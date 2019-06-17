直接遍历

Runtime: 36 ms, faster than 96.17% of Go online submissions for Max Consecutive Ones.

Memory Usage: 6.3 MB, less than 90.57% of Go online submissions for Max Consecutive Ones.

```
func findMaxConsecutiveOnes(nums []int) int {
    max, cur := 0, 0
    for _, v := range nums {
        if v == 1 {
            cur++
        } else {
            if cur > max {
                max = cur
            }
            cur = 0
        }
    }
    if cur > max {
        max = cur
    }
    return max
}
```
