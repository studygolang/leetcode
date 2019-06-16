```golang
func removeElement(nums []int, val int) {
    
    res := 0

    for _, v := range nums {
        if v != val {
            nums[res] = v
            res++
        }
    }

    return res
}
```
