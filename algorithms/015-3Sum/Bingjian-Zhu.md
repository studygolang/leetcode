排序+双指针
```golang
func threeSum(nums []int) [][]int {
	var res = [][]int{}
	lenNum := len(nums)
	if lenNum < 3 {
		return res
	}
	sort.Ints(nums)
	for i := 0; i < lenNum; i++ {
		if nums[i] > 0 {
			break
		}
		if i > 0 && nums[i] == nums[i-1] {
			continue // 去重
		}
		left := i + 1
		right := lenNum - 1
		for left < right {
			sum := nums[i] + nums[left] + nums[right]
			if sum == 0 {
				res = append(res, []int{nums[i], nums[left], nums[right]})
				for left < right && nums[left] == nums[left+1] {
					left++ // 去重
				}
				for left < right && nums[right] == nums[right-1] {
					right-- // 去重
				}
				left++
				right--
			} else if sum < 0 {
				left++
			} else if sum > 0 {
				right--
			}
		}
	}
	return res
}
```