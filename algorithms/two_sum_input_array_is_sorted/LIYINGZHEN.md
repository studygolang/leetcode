### 題目

[167. Two Sum II - Input array is sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)

### 解題思路

二元搜索法

### 代碼

```go
func twoSum(numbers []int, target int) []int {
	for i, n := range numbers {
		b := binarySearch(numbers, target-n, i+1, len(numbers)-1)
		if b != -1 {
			return []int{i + 1, b + 1}
		}
	}
	return []int{}
}

func binarySearch(nums []int, target int, left int, right int) int {
    // 注意這裡。 >= 就會錯
	if left > right {
		return -1
	}
	mid := (left + right) / 2
	if nums[mid] == target {
		return mid
	}
	if nums[mid] > target {
		return binarySearch(nums, target, left, mid-1)
	}
	return binarySearch(nums, target, mid+1, right)
}
```
