```
func majorityElement(nums []int) int {
    res, times := nums[0], 1
    for _, v := range nums {
        if res != v {
            times--            
        } else {
            times++
        } 
        if times == 0 {
                res = v
                times = 1
        }
    }
    if times >= 1 {
        return res
    }
    return 0
}
```
