### 題目

[34. Find First and Last Position of Element in Sorted Array](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)

### 解題思路

二分法。

找 start 的時候是找前一個數字的位置再加 1

### 代碼

```go
func binarySearch(nums []int, target int) int {
  l, r := 0, len(nums)-1

  for l <= r {
    m := l + (r-l)/2
    if (nums[m] < target) {
      l = m+1
    } else if (nums[m] > target) {
      r = m-1
    } else {
      l = m+1
    }
  }

  return r
}



func searchRange(nums []int, target int) []int {
  start := binarySearch(nums, target-1) + 1
  end := binarySearch(nums, target)

  if start != -1 && end != -1 && start <= end {
    return []int{start, end}
  }

  return []int{-1,-1}
}
```
