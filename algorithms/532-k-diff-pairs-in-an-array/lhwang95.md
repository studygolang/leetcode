map使我快乐

Runtime: 16 ms, faster than 99.31% of Go online submissions for K-diff Pairs in an Array.

Memory Usage: 6.3 MB, less than 49.18% of Go online submissions for K-diff Pairs in an Array.

```
func findPairs(nums []int, k int) int {
    data, res := make(map[int]int), 0
    if k < 0 {
        return 0
    }
    for _, v := range nums {
        if _, ok := data[v]; ok {
            data[v]++
        } else {
            data[v] = 1
        }
    }
    if k == 0 {
        for _, v := range data {
            if v >= 2 {
                res += 1
            }
        }
    } else {
        for v, _ := range data {
            if _, ok := data[v+k]; ok {
                res += 1
            }
        }
    }
    return res
}
```
