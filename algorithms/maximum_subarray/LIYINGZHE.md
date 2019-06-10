### 題目

[53. Maximum Subarray](https://leetcode.com/problems/maximum-subarray/)

### 解題思路

如果現在的值 (cur) 是負數，就直接拋棄，選用最新的值。
如果現在的值 (cur) 是正數，就加上最新的值。
最後都與 max 比較。

### 代碼

```go
func maxSubArray(nums []int) int {
    cur, max := nums[0], nums[0]

	for _, v := range(nums[1:]) {
        if cur < 0 {
            cur = v
        } else {
            cur += v
        }
        if cur > max {
            max = cur
        }
    }
    return max
}
```
