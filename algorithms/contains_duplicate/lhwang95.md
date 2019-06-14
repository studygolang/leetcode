Runtime: 24 ms, faster than 57.60% of Go online submissions for Contains Duplicate.

Memory Usage: 10.9 MB, less than 7.85% of Go online submissions for Contains Duplicate.

```
func containsDuplicate(nums []int) bool {
    res := make(map[int]int)
    for _, v := range nums {
        if _, ok := res[v]; ok {
            res[v]++
        } else {
            res[v] = 1
        }
        if res[v] >= 2 {
            return true
        }
    }
    return false
}
```
