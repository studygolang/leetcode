```golang
func search(nums []int, target int) int {
	low := 0
	hight := len(nums) - 1

	for low < hight {
		mid := (low + hight) / 2
		// 当[0,mid]有序时,向后规约条件
		if nums[0] <= nums[mid] && (target > nums[mid] || target < nums[0]) {
			low = mid + 1
			// 当[0,mid]发生旋转时，向后规约条件
		} else if target > nums[mid] && target < nums[0] {
			low = mid + 1
		} else {
			hight = mid
		}
	}
	if low == hight && nums[low] == target {
		return low
	}
	return -1
}
```