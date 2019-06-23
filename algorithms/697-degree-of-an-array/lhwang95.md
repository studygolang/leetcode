Runtime: 28 ms, faster than 86.02% of Go online submissions for Degree of an Array.

Memory Usage: 7 MB, less than 42.86% of Go online submissions for Degree of an Array.

```
func findShortestSubArray(nums []int) int {
    res := make(map[int][]int, 0)
    for i, v := range nums {
        if _, ok := res[v]; ok {
            res[v] = append(res[v], i-res[v][0]+1)
        } else {
            res[v] = []int{i}
        }
    }
    max, minlength := 1, 50000
    for _, v := range res {
        if len(v) >= max {
            if len(v) > max {
                max = len(v)
                minlength = v[len(v)-1]
            } else if max == len(v) && v[len(v)-1] < minlength {
                minlength = v[len(v)-1]
            } 
        }
    }
    if max == 1 {
        return 1
    } else {
        return minlength
    }
}
```
