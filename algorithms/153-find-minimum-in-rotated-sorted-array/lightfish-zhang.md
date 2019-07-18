# 寻找旋转排序数组中的最小值

## 解法

数组反转后左侧的数比右侧的大，利用这个特点，使用二分法查找

```golang
func findMin(nums []int) int {
	l, m, r := 0, 0, len(nums)-1
	for l < r {
		if nums[l] <= nums[r] {
			return nums[l]
		}
		m = (r + l) / 2
		if nums[l] <= nums[m] {
			l = m + 1
		} else {
			r = m
		}

	}
	return nums[l]
}
```