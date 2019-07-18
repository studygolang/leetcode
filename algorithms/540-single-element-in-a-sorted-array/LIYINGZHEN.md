### 題目

[540. Single Element in a Sorted Array](https://leetcode.com/problems/single-element-in-a-sorted-array/description/)

### 解題思路

二分法變種

### 代碼

```go
func singleNonDuplicate(nums []int) int {
	low, high := 0, len(nums)-1

	for low <= high {
		mid := low + (high-low)/2

		if mid-1 >= 0 && nums[mid] == nums[mid-1] {
			mid--
		} else if mid+1 < len(nums) && nums[mid] == nums[mid+1] {
		} else {
			return nums[mid]
		}

		if ((mid - low) % 2) == 1 {
			high = mid - 1
		} else {
			low = mid + 2
		}
	}

	return -1
}
```
