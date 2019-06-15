### 題目

[169. Majority Element](https://leetcode.com/problems/majority-element/)

### 解題思路

HashMap

### 代碼

```go
func majorityElement(nums []int) int {
	// 處理特殊情況
	if len(nums) == 1 {
		return nums[0]
	}

	// hashMap 記錄出現次數
	hashMap := make(map[int]int)
	half := len(nums) / 2

	for _, v := range nums {
		count, ok := hashMap[v]
		if ok {
			count++
			hashMap[v] = count
			// 超過一半立刻返回
			if count > half {
				return v
			}
		} else {
			hashMap[v] = 1
		}
	}

	return 0
}
```
