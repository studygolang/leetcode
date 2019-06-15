注意陷阱，加一可能会进位

```
func plusOne(digits []int) []int {
    cin := 1 // 设置进位标志
    length := len(digits)
    res := make([]int, length+1)
    for i := length-1; i >= 0; i-- {
        res[i+1] = digits[i] + cin
        if res[i+1] >= 10 {
            res[i+1] -= 10
            cin = 1
        } else {
            cin = 0
        }
    }
    if cin == 1 {
        res[0] = 1
    } else {
        res = res[1:]
    }
    return res
}
```
