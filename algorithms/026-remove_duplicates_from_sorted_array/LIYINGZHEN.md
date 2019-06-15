### 題目

[26. Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)

### 解題思路

這題需要兩個下標做追蹤，一個是用來取代的下標 (replaceIndex)，一個是負責往下遍歷 (currentIndex)。

currentIndex 會跟前一個值比，只要不同把值賦予給 replaceIndex。

最後 replaceIndex 就是沒有重複值 array 的長度。

### 代碼

```go
func removeDuplicates(nums []int) int {
	currentIndex, replaceIndex := 1, 1

	for currentIndex < len(nums) {
		if nums[currentIndex] != nums[currentIndex-1] {
			nums[replaceIndex] = nums[currentIndex]
			replaceIndex++
		}
		currentIndex++
	}

	return replaceIndex
}
```
