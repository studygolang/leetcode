桶排序
```golang
func firstMissingPositive(nums []int) int {
	lenNum := len(nums)

	for i := 0; i < lenNum; i++ {
		for nums[i] > 0 && nums[i] <= lenNum && nums[nums[i]-1] != nums[i] {
			nums[nums[i]-1], nums[i] = nums[i], nums[nums[i]-1]
		}
	}
	for i := 0; i < lenNum; i++ {
		if nums[i] != i+1 {
			return i + 1
		}
	}
	return lenNum + 1
}
```