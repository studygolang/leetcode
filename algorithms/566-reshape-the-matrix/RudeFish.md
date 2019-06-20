## 题目
[566. 重塑矩阵](https://leetcode-cn.com/problems/reshape-the-matrix/submissions/)

## 思路
遍历数组，将每c个数添加进原数组

## 代码
```go
func matrixReshape(nums [][]int, r int, c int) [][]int {
    // 如果不能重塑矩阵，输出原始矩阵
	if r * c != len(nums) * len(nums[0]) {
		return nums
	}
	arr := make([]int, 0)
	for _, v := range nums{
		for _, a := range v {
			arr = append(arr, a)
			// 当arr的长度和要求长度一样，添加进nums中
			if len(arr) == c {
				nums = append(nums, arr)
				// 清零
				arr = []int{}
			}
		}
	}
	// 返回新加的数组
	return nums[len(nums)-r:]
}
```
