# 213.打家劫舍

## 解法

198.house-robber题不同的是，第一个房子与最后一个房子连起来，所以求两种情况的最大值再比较，“不抢最后一个房子的”与“不抢第一个房子”，即 nums[:len(nums)-1] 与 nums[1:]

```golang
func rob(nums []int) int {
	l := len(nums)
	if l == 0 {
		return 0
	}
	if l == 1 {
		return nums[0]
	}
	res1 := _rob(nums[:l-1])
	res2 := _rob(nums[1:])
	if res1 < res2 {
		return res2
	}
	return res1
}

func _rob(nums []int) int {
	x, y := 0, nums[0]
	for _, n := range nums[1:] {
		x, y = y, x+n
		if y < x {
			y = x
		}
	}
	return y
}
```