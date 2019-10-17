二分查找
```golang
func searchInsert(nums []int, target int) int {
	lenNum := len(nums)
	if (lenNum == 1 && nums[0] == target) || lenNum == 0 {
		return 0
	}
	mid, low, hight := 0, 0, lenNum-1
	for low < hight {
		mid = (low + hight) / 2
		if target < nums[mid] {
			hight = mid
		} else if target > nums[mid] {
			low = mid + 1
		}
		if target == nums[mid] {
			return mid
		}
		if target == nums[hight] {
			return hight
		}
	}
	if target < nums[low] {
		if low != 0 {
			return low
		}
		return 0
	} else if target > nums[hight] {
		return hight + 1
	} else {
		return low + 1
	}
}
```