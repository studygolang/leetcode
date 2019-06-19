### 題目

[561. Array Partition I](https://leetcode.com/problems/array-partition-i/)

### 解題思路

先排序然後取 0, 2, 4, ... 偶數下標的值相加即可

### 代碼

```go
func arrayPairSum(nums []int) int {
	sort.Ints(nums)
	sum := 0
	for i := 0; i < len(nums); i += 2 {
		sum += nums[i]
	}
	return sum
}
```
