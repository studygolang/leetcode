4ms, 3.5mb
动态规划法，以i为结尾的子串最大值为
f(i)=nums(i), if i = 0 or f(i-1)<=0
f(i)=nums(i)+f(i-1), if i != 0 and f(i-1)>0
然后求以各个索引为结尾子串的最大值切片的最大值就是子串最大值

```
func maxSubArray(nums []int) int {
    res := ^int(^uint(0)>>1)
    length := len(nums)
    sum := make([]int, length)
    for i := 0; i < length; i++ {
        if i == 0 || sum[i-1] <= 0 {
            sum[i] = nums[i]
        }
        if i != 0 && sum[i-1] > 0 {
            sum[i] = nums[i] + sum[i-1]
        }
    }
    for _, v := range sum {
        if v > res {
            res = v
        }
    }
    return res
}
```
