### 題目

[189. Rotate Array](https://leetcode.com/problems/rotate-array/)

### 解題思路

1. 先全部翻轉
2. 翻轉下標頭到 k-1
3. 翻轉下標 k 到尾巴

*例子*

[1,2,3,4,5,6,7] and k = 3

1. [7,6,5,4,3,2,1]
2. [5,6,7,4,3,2,1]
3. [5,6,7,1,2,3,4]

### 代碼

```go
func rotate(nums []int, k int) {
	n := len(nums)

	k = k % n

	reverse(nums, 0, n-1)
	reverse(nums, 0, k-1)
	reverse(nums, k, n-1)
}

func reverse(nums []int, i int, j int) {
	for i < j {
		nums[i], nums[j] = nums[j], nums[i]
		i++
		j--
	}
}
```
