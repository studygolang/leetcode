# 46 permutations

## 解法

- 逐个插入数字来构造所有permutations
- 在使用 golang slice 时，尽量预分配适合的cap，减少内存分配频率

```golang
func permute(nums []int) [][]int {
	var ret [][]int
	if len(nums) == 0 {
		return ret
	}
	ret = make([][]int, 1, len(nums))
	ret[0] = make([]int, 1, len(nums))
	ret[0][0] = nums[0]
	for i := 1; i < len(nums); i++ {
		rows_num := len(ret)
		for j := 0; j < rows_num; j++ {
			// insert, 0~n-1
			for k := 0; k < len(ret[j]); k++ {
				item := make([]int, len(ret[j])+1, len(nums))
				copy(item[:k], ret[j][:k])
				copy(item[k+1:], ret[j][k:])
				item[k] = nums[i]
				ret = append(ret, item)
			}
			// push back, n，重复利用原来的数组
			ret[j] = append(ret[j], nums[i])
		}
	}
	return ret
}
```