直接遍历

Runtime: 32 ms, faster than 98.56% of Go online submissions for Max Consecutive Ones.

Memory Usage: 6.4 MB, less than 25.47% of Go online submissions for Max Consecutive Ones

```
func findMaxConsecutiveOnes(nums []int) int {
    max, cur := 0, 0
    for _, v := range nums {
        if v == 0 {
            cur = 0
        } else {
            cur++
            if cur > max {
                max = cur
            }
        }
    }
    return max
}
```
