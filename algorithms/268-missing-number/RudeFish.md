## 题目
[268. 缺失数字](https://leetcode-cn.com/problems/missing-number/submissions/)

## 思路一
各种if else堆叠:joy:
## 代码
```go
func missingNumber(nums []int) int {
    if len(nums) == 1 && nums[0] == 1 {
		return 0
	}
	sort.Ints(nums)

	for i:=1; i <= len(nums); {
		//fmt.Println(len(nums))
		//fmt.Println(1, len(nums))
		if i == len(nums) {
			//fmt.Println(i, len(nums))
			return nums[i-1] + 1
		}else if nums[i] != nums[i-1] + 1 {
			return nums[i-1] + 1
		} else if nums[1] == 2 {
			return 0
		}
		i++
	}
	return 0
}
```

## 思路二
用从0加到n的数，减去nums里面现有的数就是缺失的数字
## 代码
```go
func missingNumber(nums []int) int {
  sum1, sum2 := 0, len(nums)
	for i := 0; i < len(nums); i++ {
		sum2 = sum2 + i
		sum1 = sum1 + nums[i]
	}
	return sum2  - sum1
}
