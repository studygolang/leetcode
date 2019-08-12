# 最长递增子序列

## 解法一，动态规划

时间复杂度 n(n^2)，空间复杂度 n(n) 

动态规划的思路：

- 状态转移方程：if(nums[i] > nums[j]) dp[i] = max(dp[i], dp[j] + 1); ( `j<i` )
- 初始化: dp[n] = 1

```golang
func lengthOfLIS(nums []int) int {
	dp := make([]int, len(nums))
	var res int = 0
	for i := range nums {
		dp[i] = 1
		for j := 0; j < i; j++ {
			if nums[i] > nums[j] {
				dp[i] = maxInt(dp[i], dp[j]+1)
			}
		}
		res = maxInt(res, dp[i])

	}
	return res
}

func maxInt(x, y int) int {
	if x > y {
		return x
	}
	return y
}
```


## 解法二，演化子序列

时间复杂度 n(nlogn)，空间复杂度 n(n) ，虽然与上一个解法的空间复杂度一样，但那是最坏情况下，大部分情况下解法二空间复杂度更少，因为空间申请空间不会超过子序列的长度

遍历入参数组，构建子序列，一步步演化。我这里讲 “演化”，是指构建一个 ends 子序列，在遍历 nums 过程中使 ends 的长度越来越接近最优解

- 取 nums 的第一个元素，作为初始的子序列 ends
- 接下来遍历 nums 后面的元素，如果 `nums[i]` 大于 ends 最后一个元素，就追加到 ends 后面
- 如果 `nums[i]` 小于 ends 第一个元素，就用 `nums[i]` 替换 `ends[0]`
- 如果 `nums[i]` 大于 ends 第一个元素且小于 ends 最后一个元素，就用 `nums[i]` 替换 nums 递增数列中第一个不小于 `nums[i]` 的元素，这使用二分法查找位置，这个位置有可能就是 ends 最后一个元素，或者使下一次重复步骤就是替换 ends 最后一个元素

前面几个步骤琢磨下好理解，最后一个操作步骤是为什么呢，它一直使 ends 尾元素接近或等于最正确的值

```golang
func lengthOfLIS(nums []int) int {
	if len(nums) == 0 {
		return 0
	}
	ends := []int{nums[0]}
	for i := 1; i < len(nums); i++ {
		if nums[i] > ends[len(ends)-1] {
			ends = append(ends, nums[i])
		} else if nums[i] < ends[0] {
			ends[0] = nums[i]
		} else if nums[i] < ends[len(ends)-1] {
			var left, mid, right int = 0, 0, len(ends)
			for left < right {
				mid = left + (right-left)/2
				if ends[mid] < nums[i] {
					left = mid + 1
				} else {
					right = mid
				}
			}
			ends[right] = nums[i]
		}
	}
	return len(ends)
}

```
                