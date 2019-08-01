# 303 区域和检索 - 数组不可变

## 解法

动态规划，推导方程 `f(i,j) = f(0,j)-f(0,i-1)`

```golang
type NumArray struct {
	Dp []int
}

func Constructor(nums []int) NumArray {
	dp := make([]int, len(nums)+1)
	dp[0] = 0
	for i, n := range nums {
		dp[i+1] = dp[i] + n
	}
	return NumArray{Dp: dp}
}

func (this *NumArray) SumRange(i int, j int) int {
	return this.Dp[j+1] - this.Dp[i]
}
```