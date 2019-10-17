```golang
func searchRange(nums []int, target int) []int {
	lenNum := len(nums)
	if lenNum == 1 && nums[0] == target {
		return []int{0, 0}
	}
	low := 0
	hight := lenNum - 1
	start, end := -1, -1
	for low <= hight {
		mid := (low + hight) / 2
		if target < nums[mid] {
			hight = mid - 1
		} else if target > nums[mid] {
			low = mid + 1
		} else {
			start = mid
			end = mid
			for start-1 >= 0 || end+1 < lenNum {
				startEqual, endEqual := true, true
				if start-1 >= 0 && nums[start-1] == target {
					start--
				} else {
					startEqual = false
				}
				if end+1 < lenNum && nums[end+1] == target {
					end++
				} else {
					endEqual = false
				}
				if !startEqual && !endEqual {
					break
				}
			}
			break
		}
	}
	return []int{start, end}
}
```