### 題目

[153. Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/description/)

### 解題思路

Sorted 二分法求解

### 代碼

```go
func findMin(nums []int) int {
	low, high := 0, len(nums)-1

	for low < high {
		mid := low + (high-low)/2

		if nums[mid] > nums[high] {
			low = mid+1
		} else {
			high = mid
		}
	}

	return nums[low]
}
```
