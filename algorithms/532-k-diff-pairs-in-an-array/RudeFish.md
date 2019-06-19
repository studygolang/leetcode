## 题目
[532. 数组中的K-diff数对](https://leetcode-cn.com/problems/k-diff-pairs-in-an-array/submissions/)

## 思路
双重循环

## 代码
```go
func findPairs(nums []int, k int) int {
  sort.Ints(nums)
	m := make(map[int]int)
	for i, v := range nums {
		for _, u := range nums[i+1:]{
			if k == u -v {
				m[u] = v
				break
			}else if u - v >k {
				break
			}
		}
	}
	return len(m)
}
