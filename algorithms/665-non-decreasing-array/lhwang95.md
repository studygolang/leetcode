Runtime: 20 ms, faster than 98.31% of Go online submissions for Non-decreasing Array.

Memory Usage: 6.2 MB, less than 73.91% of Go online submissions for Non-decreasing Array.
```
func checkPossibility(nums []int) bool {
    time := 0
    for i:=0; i<len(nums)-1; i++ {
        if nums[i+1] - nums[i] < 0 {
            time++
        }
        if time >= 2 {
            return false
        }
    }
    time2 := 0
    if len(nums) >= 3 {
        for i:=1; i<len(nums)-1; i++ {
            if nums[i+1] - nums[i-1] < 0 {
                time2++
            }
        }
        if time2 >= 2 {
            return false
        }
    }
    return true
}
```
