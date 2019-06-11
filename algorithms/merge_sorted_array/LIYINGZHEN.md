### 題目

[88. Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/)

### 解題思路

1. replaceIndex 負責追蹤當前要取代位置的下標
2. 由後往前計算，兩邊數字互相比較，數字大的就放在 replaceIndex 的位置
3. 要小心數組不要越界

### 代碼

```go
func merge(nums1 []int, m int, nums2 []int, n int)  {
  replaceIndex := m + n - 1
  array1Target := m - 1
  array2Target := n - 1

  for array2Target >= 0 {
    if (array1Target >= 0 && nums1[array1Target] > nums2[array2Target]) {
      nums1[replaceIndex] = nums1[array1Target]
      array1Target--
    } else {
      nums1[replaceIndex] = nums2[array2Target]
      array2Target--
    }
    replaceIndex--
  }
}
```
