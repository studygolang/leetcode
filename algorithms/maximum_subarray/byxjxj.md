```golang
func maxSubArray(nums []int) int {
    
    if len(nums) == 0 {
        return 0    
    }

    res, tmp := nums[0], 0

    for _, v := range nums {
        if tmp < 0 {
            tmp = 0
        }
        tmp += v

        if res < tmp {
            res = tmp
        }
    }

    return res
}
```
