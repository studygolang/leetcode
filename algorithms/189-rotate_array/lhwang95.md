Runtime: 52 ms

Memory Usage: 7.6 MB

想不到好的解法

```
func rotate(nums []int, k int)  {
    length := len(nums)
    k = k % length
    temp := make([]int, length)
    copy(temp, nums)
    copy(nums[k:], temp[:length-k])
    copy(nums[:k], temp[length-k:])
}
```
