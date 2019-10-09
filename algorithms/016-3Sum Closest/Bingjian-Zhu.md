排序+双指针
```golang
func threeSumClosest(nums []int, target int) int {
	lenNum := len(nums)
	sort.Ints(nums)
	min := abs(nums[0] + nums[1] + nums[2] - target)
	minSum := nums[0] + nums[1] + nums[2]
	for i := 0; i < lenNum; i++ {
		left := i + 1
		right := lenNum - 1
		for left < right {
			sum := nums[i] + nums[left] + nums[right]
			tmp := abs(sum - target)
			if tmp < min {
				minSum, min = sum, tmp
			}
			if tmp == 0 {
				return minSum
			} else if sum < target {
				left++
			} else {
				right--
			}
		}
	}
	return minSum
}

func abs(x int) int {
	if x < 0 {
		return -x
	}
	return x
}
```