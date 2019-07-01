Runtime: 124 ms, faster than 97.26% of Go online submissions for Maximum Average Subarray I.

Memory Usage: 7.5 MB, less than 52.00% of Go online submissions for Maximum Average Subarray I.
```
func findMaxAverage(nums []int, k int) float64 {
    kfront, kend, sum, max := 0, k-1, 0, 0
    for i:=0; i<k; i++ {
        sum+=nums[i]
    }
    max = sum
    for kend < len(nums) - 1 {
        kend++
        sum = sum + nums[kend] - nums[kfront]
        if max < sum {
            max = sum
        }
        kfront++
    }
    return float64(max)/float64(k)
}
```
