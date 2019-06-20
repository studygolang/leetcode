## 题目
[561. 数组拆分 I](https://leetcode-cn.com/problems/array-partition-i/submissions/)

## 思路
隔一个加一下

## 代码
```go
func arrayPairSum(nums []int) int {
    sort.Ints(nums)
	v := 0
	for i:=0; i<len(nums); i=i+2{
		v += nums[i]
	}
	return v
}
