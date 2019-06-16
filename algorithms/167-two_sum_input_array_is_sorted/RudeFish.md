## 题目
[167. 两数之和 II - 输入有序数组](https://leetcode-cn.com/problems/two-sum-ii-input-array-is-sorted/submissions/)

## 思路
> 因为给定数组为升序，可以从首位相加，算出来的值过大去掉最大值，算出来的值过小去掉最小值

## 代码
```go
func twoSum3(numbers []int, target int) []int {
	for i, j := 0, len(numbers)-1; i < j; {
		if numbers[i] + numbers[j] > target {
			j--
		}
		if numbers[i] + numbers[j] < target {
			i++
		}
		if numbers[i] + numbers[j] == target {
			return []int{i+1, j+1}
		}
	}
	return nil
}
