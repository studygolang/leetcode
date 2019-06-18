
Runtime: 60 ms, faster than 99.03% of Go online submissions for Move Zeroes.
Memory Usage: 7.9 MB, less than 26.09% of Go online submissions for Move Zeroes.

思路：

1. 定义一个变量标识第一个值为0的下标元素位置

1. 遍历数组，将为0与不为0的元素交换


```go
func moveZeroes(nums []int) {
	curre := 0 // nums[curre]==0
	for i := 1; i < len(nums); i++ {
		if nums[i] != 0 {
			if nums[curre] == 0 {
				nums[curre], nums[i] = nums[i], nums[curre]
				curre++
			}
		} else {
			if nums[curre] != 0 {
				curre = i
			}
		}
	}
}
```