1、暴力解法

Runtime: 28 ms, faster than 17.94% of Go online submissions for Contains Duplicate II.

Memory Usage: 13.6 MB, less than 5.06% of Go online submissions for Contains Duplicate II.
```
func containsNearbyDuplicate(nums []int, k int) bool {
    res := make(map[int][]int)
    for i, v := range nums {
        if _, ok := res[v]; ok {
            res[v] = append(res[v], i)
        } else {
            res[v] = []int{i}
        }
    }
    for _, v := range res {
        if len(v) >= 2 {
            for i := 0; i < len(v) - 1; i++ {
                if v[i+1] - v[i] <= k {
                    return true
                }
            }
        }
    }
    return false
}
```

2、暴力改

Runtime: 16 ms, faster than 78.74% of Go online submissions for Contains Duplicate II.

Memory Usage: 9 MB, less than 30.38% of Go online submissions for Contains Duplicate II.
```
func containsNearbyDuplicate(nums []int, k int) bool {
    res := make(map[int]int)
    for i, v := range nums {
        if _, ok := res[v]; ok {
            if i - res[v] <= k {
                return true
            }
        }
        res[v] = i
    }
    return false
}
```
