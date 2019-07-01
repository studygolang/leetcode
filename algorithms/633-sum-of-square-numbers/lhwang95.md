Runtime: 0 ms, faster than 100.00% of Go online submissions for Sum of Square Numbers.

Memory Usage: 1.9 MB, less than 100.00% of Go online submissions for Sum of Square Numbers.
```
func judgeSquareSum(c int) bool {
    min, max := 0, int(math.Sqrt(float64(c)))
    for min <= max {
        res := min*min + max*max
        if res > c {
            max--
        } else if res < c {
            min++
        } else {
            return true
        }
    }
    return false
}
```
