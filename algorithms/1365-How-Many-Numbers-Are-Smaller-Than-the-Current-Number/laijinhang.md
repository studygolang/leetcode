```go
func smallerNumbersThanCurrent(nums []int) []int {
	res := make([]int, len(nums))
	for i := 0;i < len(nums);i++ {
		for j := i + 1;j < len(nums);j++ {
			if nums[i] > nums[j] {
				res[i]++
			} else if nums[i] < nums[j] {
				res[j]++
			}
		}
	}
	return res
}
```