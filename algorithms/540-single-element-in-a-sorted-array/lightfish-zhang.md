# 540. Single Element in a Sorted Array

## 解法

单身狗的位置与众不同...

```golang
func singleNonDuplicate(nums []int) int {
	l, m, r := 0, 0, len(nums)-1
	for l < r {
		m = (r-l)/2 + l
		if m%2 == 1 {
			m--
		}
		if nums[m] == nums[m+1] {
			l = m + 2
		} else {
			r = m
		}
	}
	return nums[r]
}
```