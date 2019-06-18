### 題目

[448. Find All Numbers Disappeared in an Array](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/)

### 解題思路

這題利用標記法

首先遍歷數組，把當下標數值的絕對值減去 1 得到應該標記的位置，並把對應值改成負值

最後再遍歷一次數組，找出其值不為零的下標 + 1 即可

### 代碼

```go
func findDisappearedNumbers(nums []int) []int {
    // 把數字對應的下標的值改成負數
	for _, v := range nums {
		index := int(abs(v) - 1)
		if nums[index] > 0 {
			nums[index] = -nums[index]
		}
	}

    // 找出不是負數的下標 +1 即可找出未出現的值
	res := make([]int, 0)
	for i := 0; i < len(nums); i++ {
		if nums[i] > 0 {
			res = append(res, i+1)
		}
	}

	return res
}

func abs(x int) int {
	if x < 0 {
		return -x
	}
	return x
}
```
