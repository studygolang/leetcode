## 题目
[283. 移动零](https://leetcode-cn.com/problems/move-zeroes/submissions/)
## 思路
先把不等于0的往前移，然后把后面的都等于0
## 代码
```go
func moveZeroes(nums []int)  {
  n := 0
	// 不等于0的向前移
	for _, v := range nums {
		if v != 0 {
			nums[n] = v
			n++
		}
	}
	// 0往后移
	for j := n; j < len(nums); {
		nums[j] = 0
		j++
	}
}
