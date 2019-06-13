Runtime: 12 ms, faster than 99.83% of Go online submissions for Majority Element.

Memory Usage: 5.9 MB, less than 75.24% of Go online submissions for Majority Element.

速度有点慢
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
