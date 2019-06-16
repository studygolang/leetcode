1、数学计算，适用性差

Runtime: 16 ms, faster than 96.05% of Go online submissions for Missing Number.

Memory Usage: 5.9 MB, less than 100.00% of Go online submissions for Missing Number.

```
func missingNumber(nums []int) int {
    n := len(nums)
    sumN := n*(n+1)/2
    sumM := 0
    for _, v := range nums {
        sumM += v
    }
    return sumN -sumM
}
```

2、map

Runtime: 28 ms, faster than 21.93% of Go online submissions for Missing Number.

Memory Usage: 6.2 MB, less than 6.12% of Go online submissions for Missing Number.

```
func missingNumber(nums []int) int {
    res := make(map[int]bool)
    for _, v := range nums {
        if _, ok := res[v]; !ok {
            res[v] = true
        }
    }
    i := 0
    for ; i <= len(nums); i++ {
        if _, ok := res[i]; !ok {
            break
        }
    }
    return i
}
```
