## 题目
[581. 最短无序连续子数组](https://leetcode-cn.com/problems/shortest-unsorted-continuous-subarray/)

## 思路
先排序，和未排序的比较得出

## 代码
```go
func findUnsortedSubarray(nums []int) int {
	tmp := make([]int, len(nums))
	copy(tmp, nums)
	sort.Ints(nums)
	fmt.Println(nums, tmp)
	l := 0
	for i, v := range tmp {
		if v != nums[i]{
			l = i
			for j := len(nums)-1; j > 0; j-- {
				if tmp[j] != nums[j]{
					return j+1 - l
				}
			}
		}
	}

	return 0
}
```
