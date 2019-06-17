## 题目
[448. 找到所有数组中消失的数字](https://leetcode-cn.com/problems/find-all-numbers-disappeared-in-an-array/submissions/)

## 思路
各种判断堆砌

## 代码
```go
func findDisappearedNumbers(nums []int) []int {
	l := len(nums)
  // 空直接返回
	if l == 0 {
		return nil
	}
	sort.Ints(nums)
  // 处理首部
	if nums[0] != 1 {
		for s:=1; s<nums[0]; s++ {
			nums = append(nums, s)
		}
	}
	for i := 1; i < l; i++ {
    // 处理中间部分
		if nums[i]-nums[i-1] > 1 {
			for j := nums[i-1]; j < nums[i]-1; j++ {
				nums = append(nums, j+1)
				continue
			}
      // 处理尾部有相同且有最大值
		} else if nums[l-1] == nums[l-2] && i == l-1 {
			for x := nums[i] + 1; x <= l; x++ {
				nums = append(nums, x)
			}

		}
	}
   // 处理尾部没有最大值情况
	if nums[l-1] != l && nums[l-1] != nums[l-2] {
		nums = append(nums, l)
	}
	if len(nums) == l {
		return nil
	} else {
		return nums[l:]
	}
}
